# 개요 (Overview)
Aws Elastic Beanstalk을 다른 리전으로 옮기기 위해 다시 설치 하려 했으나 s3에서 권한이 없다고 삭제가 안됨 

aws support 온라인 채팅으로 문의 -> 참고링크

참고링크 내용 보고 해결  

# 해결방법
- s3는 삭제 하려면 그전에 업로드 되어 있는 파일들을 삭제 해줘야 합니다.

- 해당 버킷 콘솔 -> 권한(Permissions) -> 버킷정책(Bucket Policy) 삭제 -참고 url 내용-

- 위 내용들 진행후 버킷을 삭제해보세요. 그래도 안되면 문의 ㄱㄱ

# 참고 url
- https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.S3.html#AWSHowTo.S3.delete-bucket