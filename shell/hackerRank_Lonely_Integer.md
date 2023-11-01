```bash

# 배열의 길이를 입력받는다
read length
# 배열을 입력받는다
read -a input_array

# 연관 배열 선언, 키와 값으로 구성되는 데이터 구
declare -A language_count

# 인덱스 0은 전체 얻기
for item in "${input_array[@]}"; do
# -z 는 null 이면 참, -n 문자가 null이 아니면 참
# null이면 1 아니면 1 더하기
  if [ -z ${language_count[$item]} ]; then
    language_count[$item]=1
  else
    language_count[$item]=$((${language_count[$item]} + 1))
  fi
done

# 연관 배열 순환하여 값이 2가 아니면 출력
for key in "${!language_count[@]}"; do
  if [ ${language_count[$key]} -ne 2 ]; then
    echo $key
  fi
done
```
