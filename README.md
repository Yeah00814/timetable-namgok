
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>특수학급 지원인력 주간 시간표</title>
    <style>
        :root {
            --primary-color: #4a6fa5;
            --secondary-color: #f4f7f6;
            --border-color: #ced4da;
            --text-color: #333;
        }

        body {
            font-family: 'Malgun Gothic', 'Apple SD Gothic Neo', sans-serif;
            background-color: #f8f9fa;
            color: var(--text-color);
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 1300px;
            margin: 0 auto;
            background: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.08);
        }

        header {
            text-align: center;
            margin-bottom: 25px;
            border-bottom: 3px solid var(--primary-color);
            padding-bottom: 15px;
        }

        header h1 {
            color: var(--primary-color);
            margin: 0;
            font-size: 28px;
        }

        .instruction-box {
            background-color: var(--secondary-color);
            border-left: 4px solid var(--primary-color);
            padding: 15px;
            margin-bottom: 25px;
            border-radius: 0 4px 4px 0;
            font-size: 14px;
            line-height: 1.6;
        }

        .tabs {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 20px;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 10px;
        }

        .tab-button {
            padding: 12px 20px;
            background-color: #e9ecef;
            border: 1px solid #dee2e6;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            font-size: 15px;
            transition: all 0.2s ease;
        }

        .tab-button.active {
            background-color: var(--primary-color);
            color: white;
            border-color: var(--primary-color);
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        .table-wrapper {
            overflow-x: auto;
            margin-bottom: 20px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            min-width: 900px;
            background: white;
        }

        th, td {
            border: 1px solid var(--border-color);
            padding: 10px;
            text-align: center;
            vertical-align: middle;
        }

        th {
            background-color: #f1f3f5;
            color: #333;
            font-weight: bold;
            font-size: 14px;
        }

        .col-period { width: 14%; }
        .col-time { width: 14%; }
        .col-day { width: 14%; }

        .cell-container {
            position: relative;
            width: 100%;
            min-height: 55px;
        }

        .editable-cell {
            width: 100%;
            min-height: 55px;
            box-sizing: border-box;
            padding: 8px;
            border: 1px dashed #ced4da;
            border-radius: 4px;
            background-color: #fafafa;
            resize: vertical;
            font-family: inherit;
            font-size: 14px;
            text-align: center;
            transition: all 0.2s;
            display: block;
        }

        .editable-cell:hover {
            border-color: #868e96;
            background-color: #fff;
        }

        .editable-cell:focus {
            border-color: var(--primary-color);
            background-color: #fff;
            outline: none;
            box-shadow: 0 0 5px rgba(74, 111, 165, 0.2);
        }

        .info-row-text {
            background-color: #fff0e6;
            color: #ff6b35;
            font-weight: bold;
            font-size: 14px;
            padding: 12px;
            border: 1px dashed #ff6b35 !important;
            border-radius: 4px;
            width: 98%;
            box-sizing: border-box;
            margin: 0 auto;
            text-align: center;
        }

        .btn-container {
            display: flex;
            justify-content: flex-end;
            gap: 10px;
            margin-top: 20px;
        }

        .btn {
            padding: 12px 22px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            font-size: 14px;
            transition: background 0.2s;
        }

        .btn-save {
            background-color: #2ec4b6;
            color: white;
        }

        .btn-save:hover {
            background-color: #25a195;
        }

        .btn-print {
            background-color: var(--primary-color);
            color: white;
        }

        .btn-print:hover {
            background-color: #3a5984;
        }

        @media print {
            body { background: white; padding: 0; }
            .container { box-shadow: none; padding: 0; max-width: 100%; }
            .instruction-box, .tabs, .btn-container { display: none !important; }
            .tab-content { display: none !important; }
            .tab-content.active { display: block !important; }
            .editable-cell { border: 1px solid #eee !important; box-shadow: none !important; padding: 4px; }
            .info-row-text { background-color: #fff0e6 !important; -webkit-print-color-adjust: exact; print-color-adjust: exact; }
            th { background-color: #e9ecef !important; -webkit-print-color-adjust: exact; print-color-adjust: exact; }
            td { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>특수학급 지원인력 주간 시간표</h1>
    </header>

    <div class="instruction-box">
        🎨 <strong>학생별 고유 음영 자동 적용:</strong> 칸 안에 내용을 입력할 때 학생 이름을 **`[민수]`**, **`[지호]`** 처럼 **대괄호`[ ]`로 감싸서 입력**하세요. 중복 없이 최대 20명까지 서로 다른 파스텔톤 배경색이 고유하게 지정됩니다.
    </div>

    <div class="tabs">
        <button class="tab-button active" onclick="openTab('teacherA')">지도사 선생님</button>
        <button class="tab-button" onclick="openTab('teacherB')">강지민 선생님</button>
        <button class="tab-button" onclick="openTab('teacherC')">서덕민 선생님</button>
        <button class="tab-button" onclick="openTab('teacherD')">협력강사 선생님</button>
    </div>

    <div id="timetable-container"></div>

    <div class="btn-container">
        <button class="btn btn-save" onclick="saveAllData()">💾 현재 설정 저장하기</button>
        <button class="btn btn-print" onclick="window.print()">🖨️ 현재 시간표 인쇄 / PDF 저장</button>
    </div>
</div>

<script>
    const teachers = ['teacherA', 'teacherB', 'teacherC', 'teacherD'];
    const teacherNames = {
        'teacherA': '지도사 선생님',
        'teacherB': '강지민 선생님',
        'teacherC': '서덕민 선생님',
        'teacherD': '협력강사 선생님'
    };

    const days = ['월', '화', '수', '목', '금'];

    const baseSlots = [
        { id: '1period', label: '1교시', time: '09:00 ~ 09:40', type: 'normal' },
        { id: '2period', label: '2교시', time: '09:50 ~ 10:30', type: 'normal' },
        { id: '3period', label: '3교시', time: '10:40 ~ 11:20', type: 'normal' },
        { id: 'block1', label: '급식1 (1,6학년)<br>4교시 (2,3,4,5학년)', time: '11:20 ~ 12:10<br>11:30 ~ 12:10', type: 'normal' },
        { id: 'block2', label: '4교시 (1,6학년)<br>급식2 (2,5학년)<br>5교시 (3,4학년)', time: '12:10 ~ 12:50<br>12:10 ~ 13:00<br>12:20 ~ 13:00', type: 'normal' },
        { id: 'block3', label: '5교시 (1,2,5,6학년)<br>급식3 (3,4학년)', time: '13:00 ~ 13:40<br>13:00 ~ 13:50', type: 'normal' },
        { id: '6period', label: '6교시', time: '13:50 ~ 14:30', type: 'normal' },
        { id: 'afterschool', label: '방과후 교실', time: '14:30 ~', type: 'normal' }
    ];

    const instructorSlots = [
        { id: '1period', label: '1교시', time: '9:00 ~ 09:40', type: 'fullRow', defaultText: '9시 40분 출근 후 2층 방과후연구실 출근부 작성' },
        { id: '2period', label: '2교시', time: '9:50 ~ 10:30', type: 'normal' },
        { id: '3period', label: '3교시', time: '10:40 ~ 11:20', type: 'normal' },
        { id: 'lunch1', label: '급식<br>(1,6학년)', time: '11:20 ~ 12:10', type: 'normal' },
        { id: 'breaktime', label: '휴게시간', time: '12:10 ~ 12:30', type: 'fullRow', defaultText: '학생 담임교사에게 인계 후 20분 휴게시간(12:10~12:30, 방과후연구실)' },
        { id: 'period4', label: '4교시<br>(1,6학년)', time: '12:10 ~ 12:50', type: 'normal' },
        { id: 'period5', label: '5교시<br>(1,2,5,6학년)', time: '13:00 ~ 13:40', type: 'normal' },
        { id: '6period', label: '6교시', time: '13:50 ~ 14:30', type: 'fullRow', defaultText: '2층 방과후연구실 출퇴근부 및 근무일지 작성 후 2시 10분 퇴근' }
    ];

    const palette = [
        { bg: '#fff3cd', border: '#ffeeba' }, { bg: '#d1ecf1', border: '#bee5eb' },
        { bg: '#d4edda', border: '#c3e6cb' }, { bg: '#f8d7da', border: '#f5c6cb' },
        { bg: '#e2e3e5', border: '#d6d8db' }, { bg: '#e1defc', border: '#d3cffc' },
        { bg: '#ffe5d9', border: '#ffcad4' }, { bg: '#d8f3dc', border: '#b7e4c7' },
        { bg: '#e0f2fe', border: '#bae6fd' }, { bg: '#fef3c7', border: '#fde68a' },
        { bg: '#fae1dd', border: '#f3c6bf' }, { bg: '#f0efa6', border: '#e6e481' },
        { bg: '#dcfce7', border: '#bbf7d0' }, { bg: '#ffedd5', border: '#fed7aa' },
        { bg: '#fae8ff', border: '#f5d0fe' }, { bg: '#e0e7ff', border: '#c7d2fe' },
        { bg: '#f3e8ff', border: '#e9d5ff' }, { bg: '#ffeaec', border: '#ffccd5' },
        { bg: '#e0f7fa', border: '#b2ebf2' }, { bg: '#f5f5dc', border: '#e6e6fa' }
    ];

    function getSlotsForTeacher(teacher) {
        if (teacher === 'teacherA') {
            return baseSlots.filter(slot => slot.id !== 'afterschool');
        } else if (teacher === 'teacherB') {
            return baseSlots
                .filter(slot => slot.id !== '6period')
                .map(slot => slot.id === 'afterschool' ? { ...slot, time: '13:40 ~ 15:00 (1시간20분)' } : slot);
        } else if (teacher === 'teacherC') {
            return baseSlots.map(slot => slot.id === 'afterschool' ? { ...slot, time: '15:00 ~ 16:20 (1시간20분)' } : slot);
        } else if (teacher === 'teacherD') {
            return instructorSlots;
        }
        return baseSlots;
    }

    let studentColors = {}; 
    let colorCounter = 0;
    let timetableData = {};

    teachers.forEach(t => {
        timetableData[t] = {};
        const slots = getSlotsForTeacher(t);
        slots.forEach(slot => {
            timetableData[t][slot.id] = {};
            if (slot.type === 'fullRow') {
                timetableData[t][slot.id]['all'] = slot.defaultText || "";
            } else {
                days.forEach(day => { timetableData[t][slot.id][day] = ""; });
            }
        });
    });

    function loadData() {
        const savedData = localStorage.getItem('special_timetable_v5');
        if (savedData) {
            try {
                timetableData = JSON.parse(savedData);
            } catch (e) {
                console.error("데이터 로드 실패", e);
            }
        }
    }

    function applyStudentInlineStyle(element, text) {
        const match = text.match(/\[(.*?)\]/);
        if (!match) {
            element.style.backgroundColor = "#fafafa";
            element.style.borderColor = "#ced4da";
            return;
        }
        
        const studentName = match[1].trim();
        if (!studentName) {
            element.style.backgroundColor = "#fafafa";
            element.style.borderColor = "#ced4da";
            return;
        }

        if (studentColors[studentName] === undefined) {
            studentColors[studentName] = colorCounter % palette.length;
            colorCounter++;
        }

        const colorIndex = studentColors[studentName];
        element.style.backgroundColor = palette[colorIndex].bg;
        element.style.borderColor = palette[colorIndex].border;
    }

    function renderTimetables() {
        const container = document.getElementById('timetable-container');
        container.innerHTML = '';

        teachers.forEach((teacher, tIdx) => {
            const activeClass = tIdx === 0 ? 'active' : '';
            const slots = getSlotsForTeacher(teacher);

            let html = `
                <div id="${teacher}" class="tab-content ${activeClass}">
                    <h2 style="color: var(--primary-color); margin-bottom: 15px;">📊 ${teacherNames[teacher]} 주간 시간표</h2>
                    <div class="table-wrapper">
                        <table>
                            <thead>
                                <tr>
                                    <th class="col-period">교시 / 운영구분</th>
                                    <th class="col-time">지원 시정(시간)</th>
                                    ${days.map(day => `<th class="col-day">${day}요일</th>`).join('')}
                                </tr>
                            </thead>
                            <tbody>
            `;

            slots.forEach(slot => {
                html += `<tr>`;
                html += `<td style="font-weight: bold; background-color: #f8f9fa;">${slot.label}</td>`;
                html += `<td style="color: #495057; font-size: 13px; background-color: #f8f9fa; font-weight: 500;">${slot.time}</td>`;
                
                if (slot.type === 'fullRow') {
                    const val = timetableData[teacher]?.[slot.id]?.__full__ || timetableData[teacher]?.[slot.id]?.[ 'all' ] || slot.defaultText || "";
                    html += `
                        <td colspan="${days.length}">
                            <input 
                                type="text" 
                                class="info-row-text" 
                                data-teacher="${teacher}" 
                                data-slot="${slot.id}" 
                                data-type="fullRow"
                                value="${val}"
                                oninput="handleFullRowInput(this)"
                            />
                        </td>
                    `;
                } else {
                    days.forEach(day => {
                        const value = timetableData[teacher]?.[slot.id]?.[day] || "";
                        html += `
                            <td>
                                <div class="cell-container">
                                    <textarea 
                                        class="editable-cell" 
                                        data-teacher="${teacher}" 
                                        data-slot="${slot.id}" 
                                        data-day="${day}"
                                        placeholder="-"
                                        oninput="handleCellInput(this)"
                                    >${value}</textarea>
                                </div>
                            </td>
                        `;
                    });
                }
                html += `</tr>`;
            });

            html += `
                            </tbody>
                        </table>
                    </div>
                </div>
            `;
            container.innerHTML += html;
        });

        document.querySelectorAll('.editable-cell').forEach(cell => {
            if(cell.value) applyStudentInlineStyle(cell, cell.value);
        });
    }

    function handleCellInput(element) {
        const teacher = element.getAttribute('data-teacher');
        const slot = element.getAttribute('data-slot');
        const day = element.getAttribute('data-day');
        const text = element.value;
        
        if (!timetableData[teacher]) timetableData[teacher] = {};
        if (!timetableData[teacher][slot]) timetableData[teacher][slot] = {};
        
        timetableData[teacher][slot][day] = text;
        applyStudentInlineStyle(element, text);
    }

    function handleFullRowInput(element) {
        const teacher = element.getAttribute('data-teacher');
        const slot = element.getAttribute('data-slot');
        const text = element.value;

        if (!timetableData[teacher]) timetableData[teacher] = {};
        if (!timetableData[teacher][slot]) timetableData[teacher][slot] = {};
        
        timetableData[teacher][slot]['all'] = text;
        timetableData[teacher][slot]['__full__'] = text; 
    }

    function saveAllData() {
        localStorage.setItem('special_timetable_v5', JSON.stringify(timetableData));
        alert('✨ 모든 변경 사항이 안전하게 브라우저에 저장되었습니다.');
    }

    function openTab(teacherId) {
        const contents = document.querySelectorAll('.tab-content');
        contents.forEach(content => content.classList.remove('active'));

        const buttons = document.querySelectorAll('.tab-button');
        buttons.forEach(button => button.classList.remove('active'));

        document.getElementById(teacherId).classList.add('active');
        
        const btnIdx = teachers.indexOf(teacherId);
        if(btnIdx > -1) { buttons[btnIdx].classList.add('active'); }
    }

    window.onload = function() {
        loadData();
        renderTimetables();
    };
</script>

</body>
</html>
