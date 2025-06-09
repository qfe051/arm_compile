# libusb를 arm용으로 빌드하는 Makefile
# 크로스 컴파일용 GCC , AR (라이브러리 생성기) 설정 
# 설치된 Tizen Studio의 경로에 따라 수정 필요 -> tizen-studio 의 기본 설치 경로.
# 절대경로 사용 or TOOLCHAIN_TIZEN 과 같은 환경 변수 설정 하기 
# :=: GNU Make의 단순 치환 (즉시 평가) 연산자
# AR: 정적 라이브러리 .a 파일을 만드는 도구 (GNU ar)

CC := /home/cammsys-em/tizen-studio/tools/arm-linux-gnueabi-gcc-9.2/bin/arm-linux-gnueabi-gcc
AR := /home/cammsys-em/tizen-studio/tools/arm-linux-gnueabi-gcc-9.2/bin/arm-linux-gnueabi-ar

# 컴파일 옵션 -> c 언어
# -O2: 최적화 옵션 (속도와 크기 균형)
# -fPIC: Position Independent Code (공유 라이브러리용 필수 옵션)
# -Wall: 모든 일반적인 경고 출력
# -Ilibsub, -Ilibsub/libusb: 헤더 파일 검색 경로 추가
CFLAGS := -O2 -fPIC -Wall -Ilibsub -Ilibsub/libusb

# 출력 파일 이름 지정
# .a 확장자는 정적 라이브러리 (archive) 
# .so 확장자는 공유 라이브러리 (shared object)
STATIC := libusb-1.0.a
SHARED := libusb-1.0.so 

# 소스/오브젝트 
# wildcard 함수는 지정된 패턴에 맞는 파일 목록을 반환 - > 알아두기 
# RCS에 있는 각 파일명에서 .c를 .o로 치환
SRCS := $(wildcard libusb/*.c)
OBJS := $(SRCS:.c=.o)

# 기본 타켓 
# .PHONY는 **"이 타겟은 실제 파일이 아니라, 항상 실행돼야 하는 가짜 이름"**이라는 의미
.PHONY: all
# all 을 사용하여 2개의 파일 빌드 지시 
all : $(STATIC) $(SHARED)

# 정적 라이브러리 생성
# $(AR) 컴파일러 사용
# rcs : r: replace, c: create, s: index 생성
# $@ : 타겟 이름, $^ : 모든 의존성 파일 libusb/*.o 전부
$(STATIC): $(OBJS)
	$(AR) rcs $@ $^

# 공유 라이브러리 생성 
# -shared 옵션을 사용하여 공유 라이브러리 생성
# .so 생각하면 쉬울 듯?
$(SHARED): $(OBJS)
	$(CC) -shared -o $@ $^

# 개별 컴파일 규칙
# $(CFLAGS) 컴파일 옵션 
# $< : 현재 규칙의 입력 파일 = .c
# $@ : 현재 규칙의 출력(타겟) 파일 = .o
# libusb/.c → libusb/.o를 자동으로 컴파일하는 핵심 규칙
%.o: %.c 
	$(CC) $(CFLAGS) -c $< -o $@

# 설치/제거용 타겟. 