#websites

2022.9월 bubble.io를 시작했다.
이것저것 만들어 보는 중...ing..

1. 심리검사 사이트 https://mbti-halloween.bubbleapps.io/version-test?debug_mode=true
팀플- 기능 구현, 개발을 맡았다. 

설명: MBTI 기반 심리 검사를 한 후, 각자에게 맞는 유형의 할로윈 코스튬을 추천해주는 사이트.

데이터 타입: <유저로그> { E/I(int), S/N(int), T/F(int), J/P(int) , MBTI결과(int), 슬러그(주소)} 
슬러그는 각자 결과 페이지를 공유할 수 있도록 고유 url을 만들기 위함이다.

구조: 누군가 페이지에 들어오면 '유저로그'라는 데이터를 생성해 심리 검사 답변을 기록한다.
유저는 각 성격 유형(E/I  S/N  T/F  J/P)을 나타내는 4개의 칸과 전체 MBTI결과를 나타내는 칸을 갖는다.
질문은 총 12개로 각 유형마다 3개씩 질문한다. (외향E/내향I 유형 질문 3개, 나머지 유형 질문도 각 3개씩)
예를 들어 E or I 를 결정짓는 질문을 제시하고, E에 해당하는 답변을 하면 유저의 E/I 데이터에 + 0(사실상 아무것도 안변함) , I에 해당하는 답변은 +1 을 한다.
이렇게 해서 결과가 0, 1, 2, 3 중  2,3 이 나오면 I에 가까운 성격  0, 1 이 나오면 E에 가까운 성격이다.
예컨대, 유저의 결과가 3(E/I), 2(S/N), 2(T/F), 3(J/P)라면 총 결과는 INTJ 유형(1111),  
        또는 결과가 1,0,1,1이라면 총결과는 ESFP유형(0000)으로 표현한다.
그렇게 정해진 유형에 따라 미리 저장해둔 캐릭터에서 같은 MBTI를 갖는 캐릭터들만을 추출해 화면에 보여준다.

한계: 카카오톡 공유 API를 사용했는데, 어떤 이유에선지 될 때가 있고 안될 때가 있다. 
휴대폰 기종에 따른 문제로 보이기도 하고, HTML 헤더 파일이 페이지로드가 완료되지 않았는데 읽히는 문제로 보이기도 한다.
사용된 코드:
<script src="https://developers.kakao.com/sdk/js/kakao.js"></script>
<script>window.Kakao.init("JAVA 앱키")</script>

<script>
  Kakao.Share.createDefaultButton({
    container: '#kakaotalk-sharing-btn',
    objectType: 'feed',
    content: {
      title: '이번 할로윈에 뭐 입지?',
      description: '#MBTI #할로윈 #코스튬 추천',
      imageUrl: 'https://ifh.cc/g/scMJKr.jpg',
      link: {
        mobileWebUrl: 'https://mbti-halloween.bubbleapps.io/version-test',
        webUrl: 'https://mbti-halloween.bubbleapps.io/version-test',
      },
    },
    buttons: [
      {
        title: '코스튬 추천 받기',
        link: {
          mobileWebUrl: '', - 동적 자료: 현재 url
          webUrl: '',',    
        },
      }
    ],
  });
</script>


2. 간단한 게시판 연습 https://work-in-koreauniv.bubbleapps.io/version-test/intro 
설명: 배포용은 아니고, 혼자 bubble.io 툴을 공부할 때 만들어 본 근로장학 근무지 정보공유 사이트이다. 에브리타임 게시판 기능을 참고했다.

데이터 타입 - 게시판{작성자, 댓글{작성자, 대댓글{작성자}}'s list} 
            - 익명관리_게시판{유저리스트(지금까지 댓글 쓴 사람들)}
            
구조: 지도에 근무지가 뜨고, 해당 근무지를 누르면 각 게시판으로 이동한다. 게시판은 근무장소마다 1개씩 + 홍보게시판 + 자유게시판이 있다.
각 게시판마다 댓글, 대댓글, 검색 기능(fuzzy search)을 만들어 놨다.
또한 게시판에 유저가 댓글을 달 때마다 댓글 단 사람들을 기록해 익명1, 익명2 이런식으로 익명을 붙여서 나타내준다.
작성자가 자신의 글에 댓글이나 대댓글을 달 경우 작성자로 뜬다. 

한계: bubble.io 의 무료버전은 최대 데이터가 200개이다. 
사실상 게시판 전체 글을 200개로 유지하는 사이트는 존재 가치가 굉장히 떨어진다.
따라서 기능 구현 후 배포를 못한다는 생각에 결국 흥미가 떨어졌다..

3. 유투브 클로닝 https://youtubecloning.bubbleapps.io/version-test
  설명: 유투브 클로닝. API를 잘 할줄 아는 형님의 도움을 받아 연습했다. 
  데이터타입: 전부 API로 데이터를 받아왔다
  
4. 다음 프로젝트 진행중...12월 전에 업로드 예정
'

꽃가루 날리기:
html head에 이거
<script src="https://tistory4.daumcdn.net/tistory/3134841/skin/images/confetti_v2.js"></script>
    
<script>
$(document).ready(function(){  
  //티스토리 공감버튼 이벤트
  function reAction(){
  	$("#startButton").trigger("click");
  	setTimeout(function(){
  		$("#stopButton").trigger("click");
  	}, 6000);
  }
  
      reAction();
});
</script>



html body 에 메인 소스
<script src="https://tistory4.daumcdn.net/tistory/3134841/skin/images/confetti_v2.js"></script>

<style>
	canvas{z-index:10;left:0;right:0;pointer-events: none;position: fixed;top: 0;transform: scale(1.1);}
</style>

<div class="buttonContainer">
	<button class="canvasBtn" id="startButton">꽃가루 휘날리기</button>	
</div>

<canvas id="canvas"></canvas>


  
  

