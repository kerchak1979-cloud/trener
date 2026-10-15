<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<title>Алгоритм ОПИ — интерактивный тренажёр</title>
<style>
  * { box-sizing: border-box; }
  body {
    font-family: 'Segoe UI', Roboto, Arial, sans-serif;
    background: #f4f6f8;
    margin: 0; padding: 24px;
    color: #2c3e50;
  }
  .container { max-width: 860px; margin: 0 auto; }
  h1 {
    font-size: 1.4em;
    background: #2c3e50;
    color: #fff;
    padding: 18px 24px;
    border-radius: 12px;
    margin-bottom: 20px;
  }
  h1 small { display: block; font-weight: 400; font-size: 0.7em; opacity: 0.8; margin-top: 6px; }

  .task {
    background: #fffbea;
    border-left: 5px solid #f39c12;
    padding: 16px 20px;
    border-radius: 8px;
    margin-bottom: 20px;
    font-size: 0.95em;
  }
  .task b { color: #b9770e; }

  .step {
    background: #fff;
    border: 2px solid #dfe6e9;
    border-radius: 12px;
    margin-bottom: 14px;
    overflow: hidden;
    transition: border-color 0.3s;
  }
  .step.current { border-color: #3498db; box-shadow: 0 0 0 3px rgba(52,152,219,0.12); }
  .step.done { border-color: #27ae60; }
  .step.error { border-color: #c0392b; }

  .step-header {
    padding: 14px 20px;
    font-weight: 600;
    display: flex; align-items: center; gap: 10px;
    background: #f8f9fa;
    font-size: 0.95em;
  }
  .step.current .step-header { background: #d6eaf8; }
  .step.done .step-header { background: #eafaf1; }
  .step.error .step-header { background: #fdedec; }

  .num {
    width: 26px; height: 26px;
    border-radius: 50%;
    background: #bdc3c7;
    color: #fff;
    display: inline-flex; align-items: center; justify-content: center;
    font-size: 0.8em; flex-shrink: 0;
  }
  .step.current .num { background: #3498db; }
  .step.done .num { background: #27ae60; }
  .step.error .num { background: #c0392b; }

  .step-body { padding: 16px 20px; display: none; }
  .step.current .step-body,
  .step.done .step-body,
  .step.error .step-body { display: block; }

  .step-body p { margin: 0 0 10px; font-size: 0.93em; }
  .step-body .ok { color: #27ae60; font-weight: 600; }
  .step-body .bad { color: #c0392b; font-weight: 600; }
  .step-body .hint { color: #7f8c8d; font-style: italic; font-size: 0.88em; }

  .btns { display: flex; gap: 10px; margin-top: 12px; flex-wrap: wrap; }
  button {
    font-family: inherit;
    font-size: 0.92em;
    padding: 10px 22px;
    border-radius: 8px;
    border: none;
    cursor: pointer;
    font-weight: 600;
    transition: 0.2s;
  }
  .btn-yes { background: #27ae60; color: #fff; }
  .btn-yes:hover { background: #219a52; }
  .btn-no { background: #e74c3c; color: #fff; }
  .btn-no:hover { background: #c0392b; }
  .btn-reset { background: #ecf0f1; color: #2c3e50; margin-top: 18px; }
  .btn-reset:hover { background: #d5dbdb; }

  .result {
    background: #eafaf1;
    border: 2px solid #27ae60;
    border-radius: 12px;
    padding: 20px 24px;
    margin-top: 18px;
    display: none;
  }
  .result.show { display: block; }
  .result h3 { margin-top: 0; color: #1e8449; }

  .code {
    display: inline-block;
    background: #2c3e50;
    color: #f1c40f;
    padding: 2px 10px;
    border-radius: 4px;
    font-family: Consolas, monospace;
    font-weight: 600;
  }
  .tag {
    display: inline-block;
    font-size: 0.72em;
    padding: 2px 8px;
    border-radius: 10px;
    background: #f39c12;
    color: #fff;
    margin-left: 6px;
    vertical-align: middle;
  }
</style>
</head>
<body>
<div class="container">

<h1>🧭 Алгоритм применения ОПИ ТН ВЭД ЕАЭС
<small>Определите подсубпозицию (6 знаков) для мягкой набивной игрушки «Солнышко»</small>
</h1>

<div class="task">
  <b>Условие:</b> Мягкая набивная игрушка, изображающая существо в виде солнышка, предназначена для игры детей от 1 года. Туловище овальное, 17 см, с лучами. Изготовлена из трикотажного полотна (100% полиэфир), набивка — 100% полиэфир. Глаза, нос, рот прошиты чёрными нитками (100% вискоза). Поставляется без упаковки.
</div>

<!-- ШАГ 1 -->
<div class="step current" id="s1">
  <div class="step-header"><span class="num">1</span> ОПИ 1 — есть ли товарная позиция, которая прямо описывает товар? <span class="tag">товарная позиция</span></div>
  <div class="step-body">
    <p><b>Что делаем:</b> ищем в тексте ТН ВЭД позицию, которая описывает <b>функцию</b> товара (игрушка для игры детей), а не материал (полиэфир, вискоза). Названия разделов и групп — только для удобства.</p>
    <p><b>Ключевой признак:</b> «игрушка для игры детей». Материал вторичен.</p>
    <p><b>Находим:</b> Раздел XX → Группа 95 «Игрушки, игры и спортивный инвентарь» → позиция <span class="code">9503</span> «Трёхколёсные велосипеды, самокаты… куклы; прочие игрушки…». Примечания к группе 95 не исключают мягкие набивные игрушки.</p>
    <div class="btns">
      <button class="btn-yes" onclick="go(1,'yes')">Да, позиция 9503 подходит</button>
      <button class="btn-no" onclick="go(1,'no')">Нет, нужно искать дальше</button>
    </div>
  </div>
</div>

<!-- ШАГ 2 -->
<div class="step" id="s2">
  <div class="step-header"><span class="num">2</span> ОПИ 2(а) — товар в некомплектном или разобранном виде? <span class="tag">некомплект</span></div>
  <div class="step-body">
    <p><b>Что делаем:</b> проверяем, не поставляется ли товар разобранным или некомплектным. Если да — классифицируем как комплектный, если он обладает основным свойством готового товара.</p>
    <p><b>Наш случай:</b> игрушка цельная, её не нужно собирать. Все части (туловище, лучи, глаза, нос, рот) уже соединены. Некомплекта нет.</p>
    <p class="bad">✘ ОПИ 2(а) не применяется.</p>
    <div class="btns">
      <button class="btn-yes" onclick="go(2,'yes')">Да, товар разобран</button>
      <button class="btn-no" onclick="go(2,'no')">Нет, товар цельный</button>
    </div>
  </div>
</div>

<!-- ШАГ 3 -->
<div class="step" id="s3">
  <div class="step-header"><span class="num">3</span> ОПИ 2(б) — смесь материалов, где позиция ссылается на материал? <span class="tag">смеси</span></div>
  <div class="step-body">
    <p><b>Что делаем:</b> проверяем, есть ли в тексте позиции ссылка на конкретный материал (например, «изделия из резины»), и состоит ли товар из смеси этого материала с другими.</p>
    <p><b>Наш случай:</b> позиция 9503 называется «игрушки». В ней <b>не упоминается материал</b>. Поэтому ОПИ 2(б) не к чему применить. Мы классифицируем по функции, а не по составу.</p>
    <p class="bad">✘ ОПИ 2(б) не применяется.</p>
    <div class="btns">
      <button class="btn-yes" onclick="go(3,'yes')">Да, позиция ссылается на материал</button>
      <button class="btn-no" onclick="go(3,'no')">Нет, позиция про игрушки, не про материал</button>
    </div>
  </div>
</div>

<!-- ШАГ 4 -->
<div class="step" id="s4">
  <div class="step-header"><span class="num">4</span> ОПИ 3 — есть ли конкуренция позиций? <span class="tag">конкуренция</span></div>
  <div class="step-body">
    <p><b>Что делаем:</b> проверяем, можно ли товар отнести к двум или более позициям. Если да — применяем ОПИ 3(а), затем 3(б), затем 3(в).</p>
    <p><b>Наш случай:</b> конкуренции нет. Позиция 9503 идеально описывает товар. Альтернативы (6307 — текстиль, 9404 — подушки, 9505 — праздничные атрибуты) не подходят, потому что функция товара — игровая.</p>
    <p class="bad">✘ ОПИ 3 не применяется.</p>
    <div class="btns">
      <button class="btn-yes" onclick="go(4,'yes')">Да, есть конкуренция</button>
      <button class="btn-no" onclick="go(4,'no')">Нет, позиция одна</button>
    </div>
  </div>
</div>

<!-- ШАГ 5 -->
<div class="step" id="s5">
  <div class="step-header"><span class="num">5</span> ОПИ 4 — товар уникален и не имеет позиции? <span class="tag">сходство</span></div>
  <div class="step-body">
    <p><b>Что делаем:</b> проверяем, есть ли вообще подходящая позиция. Если нет — ищем наиболее сходный товар.</p>
    <p><b>Наш случай:</b> мягкие игрушки существуют сотни лет. Для них есть специальная позиция 9503. ОПИ 4 — «спасательный круг» для уникальных товаров, здесь не нужен.</p>
    <p class="bad">✘ ОПИ 4 не применяется.</p>
    <div class="btns">
      <button class="btn-yes" onclick="go(5,'yes')">Да, товар уникален</button>
      <button class="btn-no" onclick="go(5,'no')">Нет, позиция есть</button>
    </div>
  </div>
</div>

<!-- ШАГ 6 -->
<div class="step" id="s6">
  <div class="step-header"><span class="num">6</span> ОПИ 5 — есть ли упаковка? <span class="tag">упаковка</span></div>
  <div class="step-body">
    <p><b>Что делаем:</b> проверяем, поставляется ли товар с упаковкой (обычной или специальной). Если да — классифицируем упаковку вместе с товаром.</p>
    <p><b>Наш случай:</b> в условии прямо сказано: «Поставляется без упаковки». Упаковки нет — классифицировать нечего.</p>
    <p class="bad">✘ ОПИ 5 не применяется.</p>
    <div class="btns">
      <button class="btn-yes" onclick="go(6,'yes')">Да, есть упаковка</button>
      <button class="btn-no" onclick="go(6,'no')">Нет, без упаковки</button>
    </div>
  </div>
</div>

<!-- ШАГ 7 -->
<div class="step" id="s7">
  <div class="step-header"><span class="num">7</span> ОПИ 6 — определяем субпозицию внутри позиции 9503 <span class="tag">субпозиция</span></div>
  <div class="step-body">
    <p><b>Что делаем:</b> внутри позиции 9503 ищем субпозицию, описывающую нашу игрушку. Сравниваем только субпозиции одного уровня.</p>
    <p><b>Ищем:</b> «игрушки, изображающие животных или других существ, кроме людей» → внутри него «набивные».</p>
    <p><b>Почему подходит:</b> игрушка мягкая, набивная, изображает существо (солнышко), не человека.</p>
    <p class="ok">✔ Субпозиция: <span class="code">9503 00</span>. Полный 10-значный код: <span class="code">9503 00 410 0</span>.</p>
  </div>
</div>

<button class="btn-reset" onclick="resetAll()">🔄 Начать заново</button>

<div class="result" id="result">
  <h3>✅ Алгоритм пройден верно!</h3>
  <p>Вы последовательно применили ОПИ 1 и ОПИ 6. Остальные правила (ОПИ 2, 3, 4, 5) не понадобились, потому что товар классифицируется на первом же шаге.</p>
  <p><b>Итог:</b> субпозиция <span class="code">9503 00</span>, полный код <span class="code">9503 00 410 0</span>.</p>
</div>

</div>

<script>
  const steps = [1,2,3,4,5,6,7].map(i => document.getElementById('s'+i));
  let current = 1;

  function go(stepNum, answer) {
    const step = document.getElementById('s'+stepNum);

    // Шаг 1: "Да" ведёт вперёд, "Нет" — ошибка
    if (stepNum === 1) {
      if (answer === 'yes') {
        step.classList.remove('current'); step.classList.add('done');
        activateStep(2);
      } else {
        step.classList.remove('current'); step.classList.add('error');
        const body = step.querySelector('.step-body');
        body.innerHTML += '<p class="bad">✘ Ошибка: позиция 9503 прямо описывает игрушку. Материал (полиэфир, вискоза) не меняет функцию. Вернитесь и выберите «Да».</p>';
        const btns = body.querySelector('.btns');
        btns.innerHTML = '<button class="btn-yes" onclick="retry(1)">Попробовать снова</button>';
      }
      return;
    }

    // Шаги 2-6: "Нет" ведёт вперёд, "Да" — ошибка
    if (stepNum >= 2 && stepNum <= 6) {
      if (answer === 'no') {
        step.classList.remove('current'); step.classList.add('done');
        activateStep(stepNum + 1);
      } else {
        step.classList.remove('current'); step.classList.add('error');
        const body = step.querySelector('.step-body');
        const explanations = {
          2: '✘ Ошибка: товар цельный, его не нужно собирать. ОПИ 2(а) не применяется.',
          3: '✘ Ошибка: позиция 9503 не ссылается на материал. ОПИ 2(б) не к чему применить.',
          4: '✘ Ошибка: конкуренции позиций нет. Позиция 9503 описывает товар полностью.',
          5: '✘ Ошибка: мягкие игрушки — не уникальный товар, для них есть позиция.',
          6: '✘ Ошибка: в условии сказано «без упаковки». ОПИ 5 не применяется.'
        };
        body.innerHTML += '<p class="bad">' + explanations[stepNum] + ' Вернитесь и выберите правильный ответ.</p>';
        const btns = body.querySelector('.btns');
        btns.innerHTML = '<button class="btn-yes" onclick="retry(' + stepNum + ')">Попробовать снова</button>';
      }
      return;
    }

    // Шаг 7 — финал
    if (stepNum === 7) {
      step.classList.remove('current'); step.classList.add('done');
      document.getElementById('result').classList.add('show');
    }
  }

  function activateStep(n) {
    current = n;
    const step = document.getElementById('s'+n);
    if (step) {
      step.classList.add('current');
      step.scrollIntoView({ behavior: 'smooth', block: 'center' });
    }
  }

  function retry(stepNum) {
    const step = document.getElementById('s'+stepNum);
    step.classList.remove('error');
    step.classList.add('current');
    // Восстанавливаем кнопки
    const body = step.querySelector('.step-body');
    const originals = {
      1: '<button class="btn-yes" onclick="go(1,\'yes\')">Да, позиция 9503 подходит</button><button class="btn-no" onclick="go(1,\'no\')">Нет, нужно искать дальше</button>',
      2: '<button class="btn-yes" onclick="go(2,\'yes\')">Да, товар разобран</button><button class="btn-no" onclick="go(2,\'no\')">Нет, товар цельный</button>',
      3: '<button class="btn-yes" onclick="go(3,\'yes\')">Да, позиция ссылается на материал</button><button class="btn-no" onclick="go(3,\'no\')">Нет, позиция про игрушки, не про материал</button>',
      4: '<button class="btn-yes" onclick="go(4,\'yes\')">Да, есть конкуренция</button><button class="btn-no" onclick="go(4,\'no\')">Нет, позиция одна</button>',
      5: '<button class="btn-yes" onclick="go(5,\'yes\')">Да, товар уникален</button><button class="btn-no" onclick="go(5,\'no\')">Нет, позиция есть</button>',
      6: '<button class="btn-yes" onclick="go(6,\'yes\')">Да, есть упаковка</button><button class="btn-no" onclick="go(6,\'no\')">Нет, без упаковки</button>'
    };
    // Удаляем добавленные пояснения об ошибке
    const badParas = body.querySelectorAll('.bad');
    badParas.forEach(p => {
      if (p.textContent.includes('Ошибка') || p.textContent.includes('Вернитесь')) p.remove();
    });
    const btns = body.querySelector('.btns');
    btns.innerHTML = originals[stepNum];
  }

  function resetAll() {
    steps.forEach(s => {
      s.classList.remove('current', 'done', 'error');
    });
    document.getElementById('result').classList.remove('show');
    activateStep(1);
  }
</script>
</body>
</html># trener
Тренажер для студентов
