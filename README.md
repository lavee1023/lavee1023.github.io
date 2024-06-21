<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Profile</title>
    <link rel="stylesheet" href="1.css">
</head>
<body>
    <div class="container">
        <div class="sidebar">
            <h1>컴퓨터공학과 20242442 고우진 홈페이지</h1>
            <h2 class="section-title" data-content="skills">나의 스킬</h2>
            <h2 class="section-title" data-content="projects">프로젝트 목록</h2>
            <h2 class="section-title" data-content="jobs">희망 직무</h2>
        </div>
        <div class="main-content" id="mainContent">
        </div>
        <div class="details-pane" id="detailsPane">
            <p id="detailsText"></p>
        </div>
    </div>
    <script src="1.js"></script>
</body>
</html>

body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    display: flex;
    height: 100vh;
    background-color: rgb(230, 230, 250);
}

.container {
    display: flex;
    width: 100%;
}

.sidebar {
    width: 250px;
    background-color: rgb(88, 88, 201);
    padding: 20px;
    box-shadow: 2px 0 5px rgba(0,0,0,0.1);
}

.sidebar h1 {
    color: rgb(255, 255, 255);
    margin-top: 0;
}

.sidebar h2 {
    color: rgb(255, 255, 255);
    margin-top: 20px;
    cursor: pointer;
}

.main-content {
    flex-grow: 1;
    padding: 20px;
}

.main-content h3 {
    color: #333;
    margin-top: 20px;
}

.main-content ul {
    list-style-type: none;
    padding: 0;
}

.main-content li {
    margin-bottom: 10px;
    cursor: pointer;
}

.main-content li:hover {
    color: rgb(0, 0, 255);
}

.main-content p {
    color: #555;
}

.details-pane {
    width: 250px;
    background-color: rgb(244, 244, 244);
    padding: 20px;
    box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);
    
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);

    font-size: 30px;
}

function showDetails(text) {
    const detailsText = document.getElementById('detailsText');

    switch(text) {
        case '로봇 전용 소프트웨어':
            detailsText.textContent = "로봇 전용 소프트웨어 프로그램을 통한 로보티즈 GP 프로그래밍";
            break;
        case '앞으로 추가할 예정':
            detailsText.textContent = "앞으로 점차 채워나갈 예정";
            break;
        case '프로젝트 1: 로봇 공학 관련 논문 읽기(예정)':
            detailsText.textContent = "실행 예정";
            break;
        case '프로젝트 2: IRO 국제로봇올림피아드 참가':
            detailsText.textContent = "본선 진출까지는 했지만 목표는 상위권 입상";
            break;
        case '프로젝트 3: 휴머노이드 자체 제작(예정)':
        case '프로젝트 4: 드론 자체 제작(예정)':
        case '프로젝트 5: 드론 정비사 자격증 취득(예정)':
            detailsText.textContent = "실행 예정";
            break;
        case '로봇 공학자':
            detailsText.innerHTML = "<strong>로봇 공학자란?</strong><br> 로봇을 설계, 제조하고 응용 분야를 다루는 직업";
            break;
        case '드론 전문가':
            detailsText.innerHTML = "<strong>드론 전문가란?</strong><br> 구체적으로는 드론 개발자가 목표,<br><strong>드론 개발자란?</strong><br> 드론의 비행을 제어하는 소프트웨어를 개발하는 직업";
            break;
    }

    const detailsPane = document.getElementById('detailsPane');
    detailsPane.style.display = 'block';
}

function hideDetailsPane() {
    const detailsPane = document.getElementById('detailsPane');
    detailsPane.style.display = 'none';
}

document.querySelectorAll('.section-title').forEach(item => {
    item.addEventListener('click', event => {
        const mainContent = document.getElementById('mainContent');

        mainContent.innerHTML = '';

        const section = event.target.dataset.content;

        let content = '';
        if (section === 'skills') {
            content = `
                <h3>스킬 목록</h3>
                <ul>
                    <li id="skill1">로봇 전용 소프트웨어</li>
                    <li id="skill2">앞으로 추가할 예정</li>
                </ul>
            `;
        } else if (section === 'projects') {
            content = `
                <h3>프로젝트 목록</h3>
                <ul>
                    <li id="project1">프로젝트 1: 로봇 공학 관련 논문 읽기(예정)</li>
                    <li id="project2">프로젝트 2: IRO 국제로봇올림피아드 참가</li>
                    <li id="project3">프로젝트 3: 휴머노이드 자체 제작(예정)</li>
                    <li id="project4">프로젝트 4: 드론 자체 제작(예정)</li>
                    <li id="project5">프로젝트 5: 드론 정비사 자격증 취득(예정)</li>
                </ul>
            `;
        } else if (section === 'jobs') {
            content = `
                <h3>직무 목록</h3>
                <ul>
                    <li id="job1">로봇 공학자</li>
                    <li id="job2">드론 전문가</li>
                </ul>
            `;
        }

        mainContent.innerHTML = content;

        hideDetailsPane();

        document.querySelectorAll('#mainContent ul li').forEach(item => {
            item.addEventListener('click', () => {
                showDetails(item.textContent);
            });
        });
    });
});

const detailsPane = document.getElementById('detailsPane');
detailsPane.style.display = 'none';
