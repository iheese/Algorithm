```bash
# cut1
# 3번째 문자 출력
while read lines; do
    echo $lines | cut -c 3;
done

# cut2
# 2,7번쨰 문자 출
while read lines; do
    echo $lines | cut -c 2,7;
done


# cut3
# 띄어쓰기, 특수 문자 문자로 인식해서 2~7번째 출
while read lines; do
    echo "$lines" | cut -c 2-7;
done

# cut4
# 문자열 4번째까지 hello > hell
while read lines; do
    echo $lines | cut -c -4
done

# cut5
# 1, 2, 3 번쨰 필드까지 출력 (tab 기준, 띄어쓰기 기준아) 
while read line; do 
    echo "$line" | cut -f -3
done


# cut6
# 문자열 13번째부터 출력
while read lines; do
    echo $lines | cut -c 13-
done

# cut7 ....?
# 띄어쓰기 기준으로 4 번재 필드 출력? 예시가 이해 안감
while read lines; do
    echo $lines | cut -f 4 -d " "
done

# cut8
# 1번째부터 3번째까지 ㄷ필드 출력
while read lines; do
    echo $lines | cut -f -3 -d " "
done


# cut9
# 띄어쓰기 구분으로 2번쨰부터 쭉 필드 출력
while read lines; do 
    echo $lines | cut -f 2- -d " ";
done
```
