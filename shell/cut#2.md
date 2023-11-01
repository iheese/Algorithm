```bash
# read 로 한 줄을 읽고 lines 변수에 저장
while read lines; do
# 현재 읽은 줄의 2.7번째 문자를 추출, cut은 문자열에서 원하는 문자 위치를 추출하는데 사용, -c 옵션을 사용하여 위치를 지정
echo $lines | cut -c 2,7;
done
```
