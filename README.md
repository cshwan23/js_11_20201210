# js_11_20201210
javascript _ 1회용 사용자 정의 객체



~~~~~~~~~~~~~~~~~~~
js_23.html
~~~~~~~~~~~~~~~~~~~
  =>[일회성 사용자 정의 객체]의 사용법을 숙지한다. 
  =>[일회성 사용자 정의 객체]란 [생성자함수] 없이 1회성으로 만들어 사용하는 객체이다.
  ------------------------------
  =>[일회성 사용자 정의 객체]의 형식
  ------------------------------
    var 객참변수 = {
      속성변수명 : 데이터
      , 메소드명 : function( [매개변수] ) { 실행구문; }
    }
    <주의> 속성변수명 : 데이터 는 0개이상 나올 수 있다.
    <주의> 메소드명 : function([매개변수]){실행구문;} 는 0개이상 나올 수 있다.
    <주의> 관용적으로 [일회성 사용자 정의 객체]에서 메소드는 잘 사용하지 않는다.
  ------------------------------
  =>[일회성 사용자 정의 객체]의 속성변수, 메소드 호출 방식.
  ------------------------------
    객참번수.속성변수명
    객참변수.메소드명(~)
    
  ------------------------------
-->
     
     
     
    <!DOCTYPE html>
    <html>
    <head><meta charset="utf-8">
      <title>일회성 사용자 정의 객체</title>
      <script type="text/javascript">


      </script>

    </head>
    <body>
      <script type="text/javascript">

        //------------------------------
        //[일회성 사용자 정의 객체]를 생성하고 객체의 메위주를 sunjuk에 저장
        //------------------------------
        var sunjuk = {

          //------------
          // 속성변수 선언
          //------------
          stu_no : 1			// 학생 번호 저장
          ,stu_name : "사오정"	// 학생 이름 저장
          ,kor : 90			// 국어 점수 저장
          ,eng : 80			// 영어 점수 저장
          ,mat : 70			// 수학 점수 저장

          //------------
          // 메소드 선언
          //------------
          // 총점을 리턴하는 메소드 선언하기
          ,getTot : function(){
            // 동료 속성변수인 kor, eng, mat 을 더한 합을 리턴
            // 동료 속성변수를 호출할 경우 this.을 붙인다.
            return this.kor + this.eng + this.mat;

          }
          // 평균을 리턴하는 메소드 선언하기
          ,getAvg : function(){
            // 동료 메소드를 호출하여 kor, eng, mat의 총점을 구한후 평균을 구해 리턴
            // 동료 메소드를 호출할 경우 this.을 붙인다.
            return this.getTot()/3;
          }

        };		

        //-----------------------
        //일회성 사용자 정의 객체의 속성변수, 메소드 호출
        //-----------------------
        document.write("[번호] : "+ sunjuk.stu_no + " ");
        document.write("[이름] : "+ sunjuk.stu_name + " ");
        document.write("[총점] : "+ sunjuk.getTot() + " ");
        document.write("[평균] : "+ sunjuk.getAvg() + "<hr>");

    //**********************************************************************

        //---------------------------------------------
        // 2차원 Array 객체 생성하고 다량의 직원 정보를 저장하기
        //---------------------------------------------
        //방법1 -2차원 배열로 뭘꺼내는지 알아보기 힘들다.

        var employees = [ [1, "김란", "부장", 100000]
                ,[2, "황보민", "부장", 90000]
                ,[3, "이성배", "과장", 80000]
                ,[4, "박인선", "대리", 30000]
                 ];

        //---------------------------------------------
        // 2차원 Array 객체 안의 직원 정보를 테이블 태그와 어울려 출력하기
        //---------------------------------------------
        document.write("<table border=1><tr><th>직원번호<th>직원명<th>직급<th>연봉");

        for(var i=0; i<employees.length; i++){

          document.write("<tr>");

          for(var j=0; j<employees[i].length; j++){

            document.write("<td>"+employees[i][j]);

          }
        }
        document.write("</table><hr>");


    //**********************************************************************


        //---------------------------------------------
        // 1차원 Array 객체 생성하고 다량의 [1회성 사용자 정의 객체]를 저장하기
        //---------------------------------------------
        //방법2- 1차원배열을 이용하여 실용적인 *사용자 정의 객체* 사용했을 때
        // 		속성변수명을 가지고 꺼낼수 있어 가독성이 훨씬 좋다.
        //		1회성 사용자 정의 객체를 사용하는 이유이다.

        var employees = [

            {
              emp_no:1
              , emp_name:"김란"
              , jikup:"부장"
              , salary:100000
              , skill:["JSP","ASP"] 
              , family:[{relation:"부",name:"사오정",age:60},{relation:"모",name:"마리드",age:54}]
            }

           ,{
            emp_no:2
            , emp_name:"황보민"
            , jikup:"부장"
            , salary:90000
            , skill:["JSP","ASP","Oracle"]
              ,family:[{relation:"부",name:"다오",age:61},{relation:"모",name:"디지니",age:55}]
            }

           ,{
            emp_no:3
            , emp_name:"이성배"
            , jikup:"과장"
            , salary:80000, skill:["JSP","Python"]
              ,family:[{relation:"부",name:"배찌",age:62},{relation:"모",name:"에띠",age:56}]
            }

           ,{
            emp_no:4
            , emp_name:"박인선"
            , jikup:"대리"
            , salary:30000
            , skill:["JSP","Delphi"]
              ,family:[{relation:"부",name:"우디",age:63},{relation:"모",name:"첸첸",age:57}]
            }
        ];

        //---------------------------------------------
        // 1차원 Array 객체 안의 [일회성 사용자 정의 객체]안의 데이터를 꺼내
        // 테이블 태그와 어울려 출력하기
        //---------------------------------------------						
        document.write("<table border=1><tr><th>직원번호<th>직원명<th>직급<th>연봉<th>스킬<th>가족");

        for(var i=0; i<employees.length; i++){

          document.write("<tr>");
          document.write("<td>"+employees[i].emp_no);
          document.write("<td>"+employees[i].emp_name);
          document.write("<td>"+employees[i].jikup);
          document.write("<td>"+employees[i].salary);
          document.write("<td>"+employees[i].skill.join("/"));

          // for(var j=0; j<employees[i].family.length; j++){
          // document.write("<hr>[관계:"+employees[i].family[j].relation+" / ");
          // document.write("이름:"+employees[i].family[j].name+" / ");
          // document.write("나이:"+employees[i].family[j].age+"]<hr> ");
          // }

          var familyArr = employees[i].family;
          var str = "";
          for(var j=0; j<familyArr.length; j++){
            str = str +"[관계]:"+familyArr[j].relation;
            str = str +"[이름]:"+familyArr[j].name;
            str = str +"[나이]:"+familyArr[j].age+"<hr>";
          }
          document.write("<td>"+str);
        }
        document.write("</table><hr>");

    //<문제 1>***************************************************************

    var xxx = { v : [3,5,7]
           ,w : { no: 1 , name : "이석" , jumsu : [77, 88, 99]}

          };
    //-----------------------------------------
    // "이석" 이란 문자 출력 방법?
    document.write( xxx.w.name + "<hr>");
    // 88 이란 숫자 출력방법?
    document.write( xxx.w.jumsu[1] + "<hr>");
    // v에 저장된 Array 객체의 배열변수 개수 출력 방법?
    document.write( xxx.v.length + "<hr>");

    //<문제 2>***************************************************************

    var eee = [ {name: function(){return "사오정";}, jumsu: [77,88,99]}

          ,[  
            { name: function(){return "저팔계";}
            ,family: { father:"비", mother:"김태희"}
            }

           ]
          ];
    //-----------------------------------------
    //"사오정" 이란 문자 출력 방법?
    document.write( eee[0].name()+"<hr>");
    //"김태희" 란 문자 출력 방법?
    document.write(eee[1][0].family.mother+"<hr>");

    //<문제 3>***************************************************************

    var ggg = {

      bbb : {
          x: [
            1,   3,   { b:"친절한찬구씨", c:[{z:[999,111]}] }
            ]
        }
      ,ccc:[[333,[7,8,9]]]	
      ,ddd:{a:[11,function(){return"강아지";}]}
    };
    //-----------------------------------------
    //"친절한찬구씨" 이란 문자 출력 방법?
    document.write(ggg.bbb.x[2].b+"<hr>");
    //"강아지" 이란 문자 출력 방법?
    document.write(ggg.ddd.a[1]()+"<hr>");
    //"8" 이란 문자 출력 방법?
    document.write(ggg.ccc[0][1][1]+"<hr>");
    //"333" 이란 문자 출력 방법?
    document.write(ggg.ccc[0][0]+"<hr>");
    //"111" 이란 문자 출력 방법?
    document.write(ggg.bbb.x[2].c[0].z[1]+"<hr>");

    //**********************************************************************


      </script>

    </body>
    </html>


















