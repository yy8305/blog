# windows imagick 설치

1. https://imagemagick.org/ 접속 -> Download 페이지 이동 -> 아래 Windows Binary Release 로 이동

2. 최신 버전이 아마 제일 위에 있을 겁니다. 그거 다운로드 (저의 경우 ImageMagick-7.0.10-49-Q16-HDRI-x64-dll.exe 다운로드 함)

3. exe 파일 실행해서 설치 진행

4. cmd.exe 에 magick -version 입력해서 동작 하는지 확인

# windows imagick php dll 설치 (with xampp)

1. https://pecl.php.net/package/imagick 접속 -> 리스트 중에 맨위에 dll 링크 클릭  
    (저의 경우 version: 3.4.4, Realeases name: imagick-3.4.4.tgz)

2. 아래 DLL List 에서 "자신의 php 버전 Thread Safe (TS) x64"  
    (저의 경우 	7.1 Thread Safe (TS) x64 설치)

3. 압축 해제 -> 폴더에 있는 php_imagick.dll 파일 C:\xampp\php\ext 로 복사

4. ImageMagickObject.dll, CORE_*.dll, IM_MOD_*.dll 파일 C:\xampp\apache\bin 로 복사

5. php.ini 편집 -> 아래 내용 맨 아래에 복사
    ```
    extension=php_imagick.dll
    ```

6. C:\xampp\apache\bin 해당 경로 윈도우 환경변수에 등록

## 참고 url
- https://ourcodeworld.com/articles/read/349/how-to-install-and-enable-the-imagick-extension-in-xampp-for-windows

---------------------------------------------------------------

# ubuntu imagick 설치

- 차례대로 진행

```
$ sudo apt install imagemagick

# sudo apt list imagemagick -a  입력시 여러 버전 확인가능

$ sudo apt install php-imagick

# sudo apt list php-magick -a  입력시 여러 버전 확인가능

$ sudo systemctl restart apache2 # 아파치 재시작

# 설치 확인1
$ php -m | grep imagick 

# 설치 되있을 경우1
imagick

# 설치 확인2
$ php -r 'phpinfo();' | grep imagick 

# 설치 되있을 경우2
/etc/php/7.2/cli/conf.d/20-imagick.ini,
 imagick
 imagick module => enabled
 imagick module version => 3.4.3RC2
 imagick classes => Imagick, ImagickDraw, ImagickPixel, ImagickPixelIterator, ImagickKernel
 imagick.locale_fix => 0 => 0
 imagick.progress_monitor => 0 => 0
 imagick.skip_version_check => 1 => 1
```

## 참고 url
- https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-install-imagemagick-for-php-on-ubuntu-18-04/

---------------------------------------------------------------

# php pdf -> image 변환 1 (Spatie\PdfToImage\Pdf)

- 설치 (※ 설치시 imagick 설치 되어있어야함)
    ```
    composer require spatie/pdf-to-image
    ```

- 사용법
    ```
    $pdf = new Spatie\PdfToImage\Pdf('dist/company_intro.pdf');

    foreach (range(1, $pdf->getNumberOfPages()) as $pageNumber) {
        $pdf->setPage($pageNumber)->saveImage('/tmp/company_intro'.$pageNumber.'.jpg');
    }
    ```

## 참고 url
- https://github.com/spatie/pdf-to-image

- https://medium.com/@freekmurze/convert-a-pdf-to-an-image-using-php-dfa8e2a921bd

---------------------------------------------------------------

# Spatie\PdfToImage\Pdf 에러

- 에러 내용  

    ```
    Message: attempt to perform an operation not allowed by the security policy `PDF'
    ```
- 해결 방법

    ```
    sudo vi /etc/ImageMagick-7/policy.xml #파일 편집

    # 이런식으로 들어 간 policy 들중에 pdf 들어간거 주석처리
    <policy domain="coder" rights="none" pattern="{PS,PS2,PS3,EPS,PDF,XPS}" />
    ```


## 참고 url
- https://bugs.archlinux.org/task/60580


---------------------------------------------------------------

# php pdf -> image 변환 2 (Imagick)

- 설치 : 맨위에 내용 참고

- 사용법
```
$images = new Imagick("dist/test.pdf");
foreach($images as $i=>$image) {
    $image->setResolution(300,300);
    $image->writeImage("/tmp/test".$i.".jpg");
}
```


---------------------------------------------------------------

# php file upload error

- 에러내용 (apache error log)
    ```
    [Tue Dec 15 09:37:56.656007 2020] [php7:warn] [pid 281813] [client 221.148.55.185:12923] PHP Warning:  File upload error - unable to create a temporary file in Unknown on line 0, referer: http://dev-hi-mandarin.sgr-clp.com/dashboard/main?SOID=102018
    ```

- 해결방법
    ```
    # php.ini 위치 확인
    $ php -r 'phpinfo();'|grep php.ini

    # ";upload_tmp_dir =" 주석 걸려 있는거 해제
    upload_tmp_dir = /tmp
    ```


## 참고 url
- https://mellowhost.com/blog/backend-log-php-warning-file-upload-error-unable-to-create-a-temporary-file-in-unknown-on-line-0.html