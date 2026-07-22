<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Historia Clínica — Cirugía Plástica</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<style>
:root{
  --brand:#1a3a5c;--brand-light:#e8f0f8;--brand-mid:#3a6fa8;
  --accent:#c9a96e;--accent-light:#fdf6ec;
  --danger:#c0392b;--danger-light:#fdf0ee;
  --success:#1d7a4e;--success-light:#eaf5ef;
  --text:#1c1c1e;--text-muted:#5a6375;--text-hint:#9aa3b0;
  --border:#dde2ea;--bg:#f5f7fa;--card:#ffffff;
  --radius:10px;--radius-sm:6px;
}
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'DM Sans',sans-serif;font-size:14px;background:var(--bg);color:var(--text);line-height:1.6;min-height:100vh;}
.page-header{background:var(--brand);color:white;padding:2rem 1.5rem 1.5rem;text-align:center;position:relative;overflow:hidden;}
.page-header::before{content:'';position:absolute;inset:0;background:repeating-linear-gradient(45deg,rgba(255,255,255,.02) 0,rgba(255,255,255,.02) 1px,transparent 1px,transparent 8px);}
.page-header h1{font-family:'DM Serif Display',serif;font-size:26px;font-weight:400;letter-spacing:.02em;position:relative;}
.page-header p{font-size:13px;opacity:.7;margin-top:.4rem;position:relative;}
.gold-line{width:40px;height:2px;background:var(--accent);margin:.75rem auto 0;}
.container{max-width:760px;margin:0 auto;padding:1.5rem 1rem 3rem}
.card{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:1.25rem 1.5rem;margin-bottom:1.25rem;}
.card-title{font-size:11px;font-weight:500;text-transform:uppercase;letter-spacing:.1em;color:var(--text-muted);padding-bottom:.65rem;margin-bottom:1rem;border-bottom:1px solid var(--border);display:flex;align-items:center;gap:8px;}
.card-title .dot{width:6px;height:6px;border-radius:50%;background:var(--accent);flex-shrink:0;}
.field{margin-bottom:.9rem}.field:last-child{margin-bottom:0}
label.fl{display:block;font-size:12px;font-weight:500;color:var(--text-muted);margin-bottom:.3rem;}
input[type=text],input[type=email],input[type=tel],input[type=date],textarea,select{width:100%;border:1px solid var(--border);border-radius:var(--radius-sm);padding:8px 12px;font-size:13.5px;font-family:'DM Sans',sans-serif;color:var(--text);background:#fafbfc;outline:none;transition:border-color .15s,background .15s;}
input:focus,textarea:focus,select:focus{border-color:var(--brand-mid);background:#fff;box-shadow:0 0 0 3px rgba(58,111,168,.08);}
textarea{resize:vertical;min-height:60px}
.row2{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.row3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px}
@media(max-width:540px){.row2,.row3{grid-template-columns:1fr}}
.cb-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(170px,1fr));gap:7px;margin-bottom:.75rem;}
.cb-item{display:flex;align-items:center;gap:8px;padding:6px 10px;border:1px solid var(--border);border-radius:var(--radius-sm);cursor:pointer;font-size:13px;transition:background .12s,border-color .12s;user-select:none;}
.cb-item:hover{background:var(--brand-light);border-color:var(--brand-mid)}
.cb-item input[type=checkbox]{width:15px;height:15px;cursor:pointer;accent-color:var(--brand);flex-shrink:0;}
.cb-item.checked{background:var(--brand-light);border-color:var(--brand-mid);color:var(--brand);}
.cb-wide{grid-column:1/-1;display:flex;align-items:center;gap:10px}.cb-wide input[type=text]{flex:1}
.card-important{background:var(--accent-light);border-color:#e6d4b0;}
.card-important .card-title{border-bottom-color:#e6d4b0;color:#7a5c20}
.card-important .dot{background:#c9a96e}
.imp-item{display:flex;align-items:flex-start;gap:10px;padding:10px 0;border-bottom:1px solid #e6d4b0;}
.imp-item:last-child{border-bottom:none}
.imp-item input[type=checkbox]{margin-top:2px;width:17px;height:17px;flex-shrink:0;accent-color:var(--brand);cursor:pointer;}
.imp-item label{font-size:13px;line-height:1.6;color:#5a4010;cursor:pointer;}
.imp-item label strong{color:var(--brand);font-weight:500}
.declaracion{background:var(--success-light);border:1px solid #a8d8be;border-radius:var(--radius);padding:1rem 1.25rem;margin-bottom:1.25rem;}
.declaracion p{font-size:13px;line-height:1.7;color:#155a37}
.declaracion strong{font-weight:500;color:var(--success)}
#sig-canvas{width:100%;height:130px;border:1.5px dashed var(--border);border-radius:var(--radius-sm);display:block;background:#fafbfc;cursor:crosshair;touch-action:none;}
#sig-canvas.has-sig{border-style:solid;border-color:var(--brand-mid)}
.sat-btns{display:flex;gap:6px;flex-wrap:wrap;margin-top:6px}
.sat-btn{padding:5px 12px;border:1px solid var(--border);border-radius:20px;font-size:12px;cursor:pointer;background:white;color:var(--text-muted);font-family:'DM Sans',sans-serif;transition:all .15s;}
.sat-btn:hover{border-color:var(--brand-mid);color:var(--brand)}
.sat-btn.active{background:var(--brand);color:white;border-color:var(--brand)}
.action-row{display:flex;gap:12px;flex-wrap:wrap;padding:1.25rem 1.5rem;background:var(--card);border:1px solid var(--border);border-radius:var(--radius);margin-bottom:.75rem;align-items:center;}
.btn{padding:10px 22px;border-radius:var(--radius-sm);font-size:13.5px;font-family:'DM Sans',sans-serif;font-weight:500;cursor:pointer;border:1.5px solid var(--brand);background:var(--brand);color:white;transition:all .15s;display:inline-flex;align-items:center;gap:7px;}
.btn:hover{background:#152e4d;border-color:#152e4d}
.btn:disabled{opacity:.5;cursor:not-allowed}
.btn-outline{background:white;color:var(--brand)}.btn-outline:hover{background:var(--brand-light)}
.btn-sm{padding:5px 12px;font-size:12px;border-radius:var(--radius-sm);border:1px solid #e8b4b0;background:white;color:var(--danger);cursor:pointer;font-family:'DM Sans',sans-serif;}
.btn-sm:hover{background:var(--danger-light)}
.hint{font-size:11.5px;color:var(--text-hint);flex:1;line-height:1.5;}
.badge-req{display:inline-block;font-size:10px;font-weight:500;background:#fdecea;color:var(--danger);padding:1px 6px;border-radius:10px;margin-left:4px;vertical-align:middle;}
.progress-wrap{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:.75rem 1.25rem;margin-bottom:1.25rem;display:flex;align-items:center;gap:12px;}
.progress-bar-outer{flex:1;height:6px;background:var(--bg);border-radius:3px;overflow:hidden}
.progress-bar-inner{height:100%;background:var(--brand);border-radius:3px;transition:width .3s}
.progress-label{font-size:12px;color:var(--text-muted);white-space:nowrap}
#toast{position:fixed;bottom:1.5rem;right:1.5rem;background:var(--brand);color:white;padding:.75rem 1.25rem;border-radius:var(--radius-sm);font-size:13px;font-weight:500;opacity:0;transform:translateY(8px);transition:all .25s;pointer-events:none;z-index:999;max-width:300px;line-height:1.5;}
#toast.show{opacity:1;transform:translateY(0)}
.spinner{display:none;width:15px;height:15px;border:2px solid rgba(255,255,255,.35);border-top-color:white;border-radius:50%;animation:spin .7s linear infinite;flex-shrink:0;}
@keyframes spin{to{transform:rotate(360deg)}}
</style>
</head>
<body>

<div class="page-header">
  <h1>Historia Clínica</h1>
  <p>Cirugía Plástica · Formulario de paciente</p>
  <div class="gold-line"></div>
</div>

<div class="container">

  <div class="progress-wrap">
    <span class="progress-label" id="prog-label">Completado 0%</span>
    <div class="progress-bar-outer"><div class="progress-bar-inner" id="prog-bar" style="width:0%"></div></div>
  </div>

  <!-- Certificado de valoración -->
  <div class="card" style="border-color:#c9a96e;background:linear-gradient(135deg,#fdf9f2 0%,#fdf6ec 100%);">
    <div class="card-title" style="color:#7a5c20;border-bottom-color:#e6d4b0;">
      <span class="dot" style="background:#c9a96e"></span> Certificado de valoración — leer antes de continuar
    </div>
    <p style="font-size:13px;line-height:1.75;color:#5a4010;margin-bottom:1rem;">
      Antes de completar este formulario, confirme que ha leído y acepta las siguientes condiciones relacionadas con su valoración:
    </p>
    <div style="display:flex;flex-direction:column;gap:10px;margin-bottom:1rem;">
      <label style="display:flex;align-items:flex-start;gap:10px;padding:10px 12px;border:1px solid #e6d4b0;border-radius:8px;background:white;cursor:pointer;">
        <input type="checkbox" id="cert1" style="margin-top:2px;width:17px;height:17px;flex-shrink:0;accent-color:#1a3a5c;cursor:pointer;">
        <span style="font-size:13px;line-height:1.6;color:#5a4010;">
          Entiendo y acepto que el <strong style="color:#1a3a5c;">costo de la valoración no es reembolsable</strong>, independientemente del resultado de la consulta o de la decisión de proceder o no con el procedimiento.
        </span>
      </label>
      <label style="display:flex;align-items:flex-start;gap:10px;padding:10px 12px;border:1px solid #e6d4b0;border-radius:8px;background:white;cursor:pointer;">
        <input type="checkbox" id="cert2" style="margin-top:2px;width:17px;height:17px;flex-shrink:0;accent-color:#1a3a5c;cursor:pointer;">
        <span style="font-size:13px;line-height:1.6;color:#5a4010;">
          Entiendo que la valoración podrá realizarse de forma <strong style="color:#1a3a5c;">presencial o virtual</strong>, según las necesidades y criterio del médico o del paciente, y que ambas modalidades tienen la misma validez clínica.
        </span>
      </label>
    </div>
    <p style="font-size:11.5px;color:#9aa3b0;margin-top:.25rem;">Debe marcar ambas casillas para continuar con el formulario.</p>
  </div>

  <!-- Datos personales -->
  <div class="card">
    <div class="card-title"><span class="dot"></span> Datos personales</div>
    <div class="row2">
      <div class="field"><label class="fl">Nombre completo <span class="badge-req">requerido</span></label><input type="text" id="f-nombre" placeholder="Apellidos y nombre"></div>
      <div class="field"><label class="fl">Fecha de nacimiento</label><input type="date" id="f-dob"></div>
    </div>
    <div class="row3">
      <div class="field"><label class="fl">Teléfono</label><input type="tel" id="f-tel" placeholder="+506 0000-0000"></div>
      <div class="field"><label class="fl">Correo electrónico</label><input type="email" id="f-email" placeholder="correo@ejemplo.com"></div>
      <div class="field"><label class="fl">Cédula / ID <span class="badge-req">requerido</span></label><input type="text" id="f-cedula" placeholder="000000000"></div>
    </div>
  </div>

  <!-- Patológicos -->
  <div class="card">
    <div class="card-title"><span class="dot"></span> Antecedentes personales patológicos</div>
    <div class="cb-grid">
      <label class="cb-item"><input type="checkbox" name="pat" value="Diabetes"> Diabetes</label>
      <label class="cb-item"><input type="checkbox" name="pat" value="Hipertensión"> Hipertensión</label>
      <label class="cb-item"><input type="checkbox" name="pat" value="Cardiopatía"> Cardiopatía</label>
      <label class="cb-item"><input type="checkbox" name="pat" value="Enf. tiroidea"> Enf. tiroidea</label>
      <label class="cb-item"><input type="checkbox" name="pat" value="Coagulopatía"> Coagulopatía</label>
      <label class="cb-item"><input type="checkbox" name="pat" value="Cáncer"> Cáncer</label>
      <label class="cb-item"><input type="checkbox" name="pat" value="Autoinmune"> Autoinmune</label>
      <label class="cb-item"><input type="checkbox" name="pat" value="VIH/SIDA"> VIH / SIDA</label>
      <label class="cb-item"><input type="checkbox" name="pat" value="Lupus"> Lupus</label>
      <label class="cb-item"><input type="checkbox" name="pat" value="Asma/EPOC"> Asma / EPOC</label>
      <label class="cb-item"><input type="checkbox" name="pat" value="Anemia"> Anemia</label>
      <label class="cb-item"><input type="checkbox" name="pat" value="Ninguno"> Ninguno</label>
      <div class="cb-item cb-wide"><span style="white-space:nowrap;font-size:12px;color:var(--text-muted)">Otro:</span><input type="text" id="pat-otro" placeholder="especifique"></div>
    </div>
  </div>

  <!-- No patológicos -->
  <div class="card">
    <div class="card-title"><span class="dot"></span> Antecedentes personales no patológicos</div>
    <div class="cb-grid">
      <label class="cb-item"><input type="checkbox" name="nopat" value="Tabaquismo"> Tabaquismo</label>
      <label class="cb-item"><input type="checkbox" name="nopat" value="Alcohol"> Consumo de alcohol</label>
      <label class="cb-item"><input type="checkbox" name="nopat" value="Sedentarismo"> Sedentarismo</label>
      <label class="cb-item"><input type="checkbox" name="nopat" value="Ejercicio regular"> Ejercicio regular</label>
      <label class="cb-item"><input type="checkbox" name="nopat" value="Drogas"> Uso de drogas</label>
      <label class="cb-item"><input type="checkbox" name="nopat" value="Ninguno"> Ninguno</label>
    </div>
    <div class="field"><label class="fl">Si marcó drogas, ¿cuáles?</label><input type="text" id="drogas-cuales" placeholder="especifique"></div>
    <div class="field"><label class="fl">Observaciones adicionales</label><textarea id="nopat-obs" placeholder="..."></textarea></div>
  </div>

  <!-- Anticonceptivos -->
  <div class="card">
    <div class="card-title"><span class="dot"></span> Anticonceptivos</div>
    <div class="cb-grid">
      <label class="cb-item"><input type="checkbox" name="ac" value="Pastillas orales"> Pastillas orales</label>
      <label class="cb-item"><input type="checkbox" name="ac" value="Inyección hormonal"> Inyección hormonal</label>
      <label class="cb-item"><input type="checkbox" name="ac" value="Parche hormonal"> Parche hormonal</label>
      <label class="cb-item"><input type="checkbox" name="ac" value="DIU"> DIU</label>
      <label class="cb-item"><input type="checkbox" name="ac" value="Implante subdérmico"> Implante subdérmico</label>
      <label class="cb-item"><input type="checkbox" name="ac" value="Condón/barrera"> Condón / barrera</label>
      <label class="cb-item"><input type="checkbox" name="ac" value="Ninguno"> Ninguno</label>
    </div>
    <div class="field"><label class="fl">¿Cuál método / marca?</label><input type="text" id="ac-cual" placeholder="especifique"></div>
  </div>

  <!-- Alergias -->
  <div class="card">
    <div class="card-title"><span class="dot"></span> Alergias</div>
    <div class="row2">
      <div class="field"><label class="fl">Alergias a medicamentos</label><textarea id="alerg-med" placeholder="ej. penicilina, ibuprofeno…"></textarea></div>
      <div class="field"><label class="fl">Alergias a alimentos / látex</label><textarea id="alerg-alim" placeholder="ej. mariscos, látex…"></textarea></div>
    </div>
    <div class="field"><label class="fl">Reacciones anteriores a anestesia</label><input type="text" id="alerg-anest" placeholder="describa si aplica"></div>
  </div>

  <!-- Ginecológico -->
  <div class="card">
    <div class="card-title"><span class="dot"></span> Antecedentes ginecológicos</div>
    <div class="row3">
      <div class="field"><label class="fl">Fecha última menstruación</label><input type="date" id="gyn-fum"></div>
      <div class="field"><label class="fl">Embarazos</label><input type="text" id="gyn-emb" placeholder="nº"></div>
      <div class="field"><label class="fl">Partos vaginales</label><input type="text" id="gyn-pv" placeholder="nº"></div>
    </div>
    <div class="row3">
      <div class="field"><label class="fl">Cesáreas</label><input type="text" id="gyn-ces" placeholder="nº"></div>
      <div class="field"><label class="fl">Abortos</label><input type="text" id="gyn-ab" placeholder="nº"></div>
      <div class="field"><label class="fl">¿Menopausia?</label>
        <select id="gyn-meno"><option value="">-- seleccione --</option><option>No</option><option>Sí</option><option>Perimenopausia</option></select>
      </div>
    </div>
    <div class="field"><label class="fl">Observaciones ginecológicas</label><textarea id="gyn-obs" placeholder="..."></textarea></div>
  </div>

  <!-- Cirugías de salud -->
  <div class="card">
    <div class="card-title"><span class="dot"></span> Antecedentes quirúrgicos — cirugías de salud</div>
    <div class="field"><label class="fl">Cirugías previas por motivos de salud (tipo y año)</label><textarea id="qx-salud" placeholder="ej. apendicectomía 2018, cesárea 2020…"></textarea></div>
    <div class="field"><label class="fl">Medicamentos actuales</label><textarea id="qx-meds" placeholder="nombre, dosis y frecuencia de cada medicamento"></textarea></div>
  </div>

  <!-- Cirugía plástica -->
  <div class="card">
    <div class="card-title"><span class="dot"></span> Antecedentes quirúrgicos — cirugía plástica</div>
    <div class="row2">
      <div class="field"><label class="fl">Procedimiento realizado</label><input type="text" id="cp-proc" placeholder="ej. rinoplastia, liposucción…"></div>
      <div class="field"><label class="fl">Fecha aproximada</label><input type="date" id="cp-fecha"></div>
    </div>
    <div class="row2">
      <div class="field"><label class="fl">Médico que la realizó</label><input type="text" id="cp-medico" placeholder="nombre del cirujano"></div>
      <div class="field"><label class="fl">Clínica / lugar</label><input type="text" id="cp-lugar" placeholder="nombre del centro médico"></div>
    </div>
    <div class="field">
      <label class="fl">¿Qué tan satisfecha quedó con esa cirugía?</label>
      <div class="sat-btns" id="sat-group">
        <button type="button" class="sat-btn" data-val="1">1 — Muy insatisfecha</button>
        <button type="button" class="sat-btn" data-val="2">2 — Insatisfecha</button>
        <button type="button" class="sat-btn" data-val="3">3 — Regular</button>
        <button type="button" class="sat-btn" data-val="4">4 — Satisfecha</button>
        <button type="button" class="sat-btn" data-val="5">5 — Muy satisfecha</button>
        <button type="button" class="sat-btn" data-val="N/A">No aplica</button>
      </div>
      <input type="hidden" id="cp-sat" value="">
    </div>
    <div class="field"><label class="fl">Comentarios sobre la cirugía anterior</label><textarea id="cp-obs" placeholder="complicaciones, resultados, expectativas…"></textarea></div>
  </div>

  <!-- Indicaciones -->
  <div class="card card-important">
    <div class="card-title"><span class="dot"></span> Indicaciones importantes — marque cada punto leído y entendido</div>
    <div class="imp-item">
      <input type="checkbox" id="ind1">
      <label for="ind1">Entiendo que si tomo <strong>pastillas anticonceptivas o inyecciones hormonales (tratamiento hormonal)</strong>, debo suspenderlas mínimo <strong>2 semanas antes</strong> de la cirugía y no retomarlas hasta después de <strong>1 mes</strong> de recuperación.</label>
    </div>
    <div class="imp-item">
      <input type="checkbox" id="ind2">
      <label for="ind2">Entiendo que el <strong>cigarrillo y las drogas están estrictamente prohibidos</strong> antes de la cirugía y durante toda la recuperación postoperatoria.</label>
    </div>
    <div class="imp-item">
      <input type="checkbox" id="ind3">
      <label for="ind3">Entiendo que debo <strong>suspender el consumo de alcohol mínimo 1 semana antes</strong> de la cirugía.</label>
    </div>
    <div class="imp-item">
      <input type="checkbox" id="ind4">
      <label for="ind4">Entiendo que debo evitar <strong>viajes y cargas pesadas durante 1 a 2 meses</strong> después de la cirugía.</label>
    </div>
    <div class="imp-item">
      <input type="checkbox" id="ind5">
      <label for="ind5">Entiendo que si tengo algún <strong>déficit nutricional</strong>, debo comunicárselo al médico antes del procedimiento.</label>
    </div>
    <div class="imp-item">
      <input type="checkbox" id="ind6">
      <label for="ind6">Entiendo que <strong>no cumplir con estas indicaciones puede ser causa de suspensión o postergación de la cirugía</strong>, tanto en la fase preoperatoria como en la postoperatoria.</label>
    </div>
  </div>

  <!-- Declaración -->
  <div class="declaracion">
    <p>Declaro que la información suministrada es verídica y completa. Entiendo que <strong>no seguir las indicaciones médicas puede comprometer todas las etapas de la cirugía</strong>, tanto las previas como las posteriores. Asimismo, reconozco que los <strong>presupuestos son aproximados y sujetos a cambio</strong> según situaciones alternas que puedan presentarse.</p>
  </div>

  <!-- Firma -->
  <div class="card">
    <div class="card-title"><span class="dot"></span> Firma, nombre y cédula</div>
    <div class="row3" style="margin-bottom:.9rem">
      <div class="field"><label class="fl">Nombre completo <span class="badge-req">requerido</span></label><input type="text" id="sign-nombre" placeholder="igual que su cédula"></div>
      <div class="field"><label class="fl">Cédula / ID <span class="badge-req">requerido</span></label><input type="text" id="sign-cedula" placeholder="000000000"></div>
      <div class="field"><label class="fl">Fecha</label><input type="date" id="sign-fecha"></div>
    </div>
    <label class="fl">Firma (dibuje con su dedo o mouse)</label>
    <canvas id="sig-canvas"></canvas>
    <div style="margin-top:6px"><button type="button" class="btn-sm" id="btn-clear">Borrar firma</button></div>
  </div>

  <!-- Botones -->
  <div class="action-row">
    <button type="button" class="btn" id="btn-send">
      <span class="spinner" id="spin1"></span>
      <span id="lbl-send">Generar PDF y enviar</span>
    </button>
    <button type="button" class="btn btn-outline" id="btn-download">
      <span class="spinner" id="spin2"></span>
      <span id="lbl-dl">Solo descargar PDF</span>
    </button>
    <span class="hint">El PDF incluye todos los datos y su firma. Se descarga automáticamente y se abre su correo para adjuntarlo.</span>
  </div>

</div>
<div id="toast"></div>

<script>
// ── CONFIG ── cambia este correo por el tuyo ──────────────────────
const DOCTOR_EMAIL = 'TU-CORREO@AQUI.COM';
// ─────────────────────────────────────────────────────────────────

document.getElementById('sign-fecha').value = new Date().toISOString().split('T')[0];

// Checkbox visual
document.querySelectorAll('.cb-item input[type=checkbox]').forEach(cb => {
  cb.addEventListener('change', function() {
    this.closest('.cb-item').classList.toggle('checked', this.checked);
    updateProgress();
  });
});

// Satisfaction
document.getElementById('sat-group').querySelectorAll('.sat-btn').forEach(btn => {
  btn.addEventListener('click', function() {
    document.getElementById('sat-group').querySelectorAll('.sat-btn').forEach(b => b.classList.remove('active'));
    this.classList.add('active');
    document.getElementById('cp-sat').value = this.dataset.val;
  });
});

// Signature
const canvas = document.getElementById('sig-canvas');
const ctx = canvas.getContext('2d');
let drawing = false, lx = 0, ly = 0, hasSig = false;

function resizeCanvas() {
  const dpr = window.devicePixelRatio || 1;
  const rect = canvas.getBoundingClientRect();
  const saved = hasSig ? canvas.toDataURL() : null;
  canvas.width = rect.width * dpr;
  canvas.height = rect.height * dpr;
  ctx.scale(dpr, dpr);
  ctx.strokeStyle = '#1a3a5c'; ctx.lineWidth = 2.2; ctx.lineCap = 'round'; ctx.lineJoin = 'round';
  if (saved) { const img = new Image(); img.onload = () => ctx.drawImage(img, 0, 0, rect.width, rect.height); img.src = saved; }
}
window.addEventListener('load', resizeCanvas);
window.addEventListener('resize', resizeCanvas);

function getPos(e) {
  const r = canvas.getBoundingClientRect();
  if (e.touches) return { x: e.touches[0].clientX - r.left, y: e.touches[0].clientY - r.top };
  return { x: e.clientX - r.left, y: e.clientY - r.top };
}
canvas.addEventListener('mousedown', e => { drawing = true; const p = getPos(e); lx = p.x; ly = p.y; });
canvas.addEventListener('mousemove', e => {
  if (!drawing) return;
  const p = getPos(e);
  ctx.beginPath(); ctx.moveTo(lx, ly); ctx.lineTo(p.x, p.y); ctx.stroke();
  lx = p.x; ly = p.y; hasSig = true; canvas.classList.add('has-sig');
});
canvas.addEventListener('mouseup', () => drawing = false);
canvas.addEventListener('mouseleave', () => drawing = false);
canvas.addEventListener('touchstart', e => { e.preventDefault(); drawing = true; const p = getPos(e); lx = p.x; ly = p.y; }, { passive: false });
canvas.addEventListener('touchmove', e => {
  e.preventDefault(); if (!drawing) return;
  const p = getPos(e);
  ctx.beginPath(); ctx.moveTo(lx, ly); ctx.lineTo(p.x, p.y); ctx.stroke();
  lx = p.x; ly = p.y; hasSig = true; canvas.classList.add('has-sig');
}, { passive: false });
canvas.addEventListener('touchend', () => drawing = false);
document.getElementById('btn-clear').addEventListener('click', () => {
  const r = canvas.getBoundingClientRect();
  ctx.clearRect(0, 0, r.width, r.height);
  hasSig = false; canvas.classList.remove('has-sig');
});

// Progress
function updateProgress() {
  const ids = ['f-nombre','f-dob','f-tel','f-email','f-cedula','sign-nombre','sign-cedula'];
  let filled = 0, total = ids.length + 3 + 6 + 2;
  ids.forEach(id => { const el = document.getElementById(id); if (el && el.value.trim()) filled++; });
  ['pat','nopat','ac'].forEach(n => { if (document.querySelectorAll(`input[name="${n}"]:checked`).length > 0) filled++; });
  for (let i = 1; i <= 6; i++) { const el = document.getElementById('ind' + i); if (el && el.checked) filled++; }
  ['cert1','cert2'].forEach(id => { const el = document.getElementById(id); if (el && el.checked) filled++; });
  const pct = Math.round(filled / total * 100);
  document.getElementById('prog-bar').style.width = pct + '%';
  document.getElementById('prog-label').textContent = 'Completado ' + pct + '%';
}
document.querySelectorAll('input,textarea,select').forEach(el => { el.addEventListener('input', updateProgress); el.addEventListener('change', updateProgress); });
for (let i = 1; i <= 6; i++) { const el = document.getElementById('ind' + i); if (el) el.addEventListener('change', updateProgress); }
['cert1','cert2'].forEach(id => { const el = document.getElementById(id); if (el) el.addEventListener('change', updateProgress); });

// Toast
function showToast(msg, dur = 4000) {
  const t = document.getElementById('toast');
  t.textContent = msg; t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), dur);
}

// Helpers
const g = id => (document.getElementById(id) || {}).value || '';
const cbs = name => Array.from(document.querySelectorAll(`input[name="${name}"]:checked`)).map(c => c.value).join(', ') || 'Ninguno';

// ─── PDF BUILDER ─────────────────────────────────────────────────
function buildPDF() {
  const { jsPDF } = window.jspdf;
  const doc = new jsPDF({ unit: 'mm', format: 'a4' });
  const W = 210, PL = 14, PR = 14, CW = W - PL - PR;
  let y = 0;

  function newPage() { doc.addPage(); y = 15; }
  function chk(need = 8) { if (y + need > 282) newPage(); }

  // Header
  doc.setFillColor(26, 58, 92);
  doc.rect(0, 0, W, 30, 'F');
  doc.setTextColor(255, 255, 255);
  doc.setFont('helvetica', 'bold'); doc.setFontSize(15);
  doc.text('HISTORIA CLÍNICA — CIRUGÍA PLÁSTICA', W / 2, 13, { align: 'center' });
  doc.setFont('helvetica', 'normal'); doc.setFontSize(9);
  doc.text('Formulario de paciente · Información confidencial', W / 2, 20, { align: 'center' });
  doc.setDrawColor(201, 169, 110); doc.setLineWidth(0.8);
  doc.line(W / 2 - 18, 24, W / 2 + 18, 24);
  doc.setTextColor(30, 30, 30);
  y = 36;

  function secTitle(t) {
    chk(12);
    doc.setFillColor(232, 240, 248);
    doc.roundedRect(PL, y, CW, 7, 1, 1, 'F');
    doc.setFont('helvetica', 'bold'); doc.setFontSize(8);
    doc.setTextColor(26, 58, 92);
    doc.text(t.toUpperCase(), PL + 3, y + 5);
    doc.setTextColor(30, 30, 30);
    y += 10;
  }

  function row(label, value) {
    chk(6);
    doc.setFont('helvetica', 'normal'); doc.setFontSize(8.5);
    doc.setTextColor(90, 99, 117); doc.text(label + ':', PL + 2, y);
    doc.setTextColor(30, 30, 30);
    const lines = doc.splitTextToSize(value || '—', CW - 58);
    doc.text(lines, PL + 56, y);
    y += Math.max(5, lines.length * 4.5);
  }

  function block(label, value) {
    chk(6);
    doc.setFont('helvetica', 'bold'); doc.setFontSize(8.5);
    doc.setTextColor(90, 99, 117); doc.text(label + ':', PL + 2, y); y += 4.5;
    doc.setFont('helvetica', 'normal'); doc.setTextColor(30, 30, 30);
    const lines = doc.splitTextToSize(value || '—', CW - 5);
    chk(lines.length * 4.5);
    doc.text(lines, PL + 4, y);
    y += lines.length * 4.5 + 2;
  }

  function div() { chk(5); doc.setDrawColor(221, 226, 234); doc.setLineWidth(0.3); doc.line(PL, y, PL + CW, y); y += 5; }

  function indLine(id, text) {
    const checked = !!(document.getElementById(id) && document.getElementById(id).checked);
    chk(8);
    doc.setDrawColor(26, 58, 92); doc.setLineWidth(0.5);
    doc.rect(PL + 1, y - 3.8, 3.8, 3.8);
    if (checked) {
      doc.setFont('helvetica', 'bold'); doc.setFontSize(8); doc.setTextColor(26, 58, 92);
      doc.text('X', PL + 1.9, y - 0.6);
    }
    doc.setFont('helvetica', 'normal'); doc.setFontSize(8.5); doc.setTextColor(80, 64, 16);
    const lines = doc.splitTextToSize(text, CW - 8);
    chk(lines.length * 4.5);
    doc.text(lines, PL + 7, y);
    y += lines.length * 4.5 + 2;
  }

  // ── Certificado de valoración ──
  const cert1 = !!(document.getElementById('cert1') && document.getElementById('cert1').checked);
  const cert2 = !!(document.getElementById('cert2') && document.getElementById('cert2').checked);
  doc.setFillColor(253, 246, 236);
  doc.roundedRect(PL, y, CW, 30, 1.5, 1.5, 'F');
  doc.setDrawColor(201, 169, 110); doc.setLineWidth(0.5);
  doc.roundedRect(PL, y, CW, 30, 1.5, 1.5, 'S');
  doc.setFont('helvetica', 'bold'); doc.setFontSize(8); doc.setTextColor(122, 92, 32);
  doc.text('CERTIFICADO DE VALORACIÓN', PL + 3, y + 5.5);
  doc.setFont('helvetica', 'normal'); doc.setFontSize(8.5); doc.setTextColor(80, 64, 16);
  // checkbox 1
  doc.setDrawColor(26, 58, 92); doc.setLineWidth(0.5);
  doc.rect(PL + 3, y + 9, 3.5, 3.5);
  if (cert1) { doc.setFont('helvetica','bold'); doc.setFontSize(8); doc.setTextColor(26,58,92); doc.text('X', PL + 3.8, y + 12); }
  doc.setFont('helvetica','normal'); doc.setFontSize(8.5); doc.setTextColor(80, 64, 16);
  const c1lines = doc.splitTextToSize('El costo de la valoración no es reembolsable, independientemente del resultado o de la decisión de proceder con el procedimiento.', CW - 12);
  doc.text(c1lines, PL + 9, y + 12.5);
  // checkbox 2
  doc.rect(PL + 3, y + 19, 3.5, 3.5);
  if (cert2) { doc.setFont('helvetica','bold'); doc.setFontSize(8); doc.setTextColor(26,58,92); doc.text('X', PL + 3.8, y + 22); }
  doc.setFont('helvetica','normal'); doc.setFontSize(8.5); doc.setTextColor(80, 64, 16);
  const c2lines = doc.splitTextToSize('La valoración podrá realizarse de forma presencial o virtual, según las necesidades del médico o del paciente, con la misma validez clínica.', CW - 12);
  doc.text(c2lines, PL + 9, y + 22.5);
  y += 35;
  div();

  // ── Sections ──
  secTitle('1. Datos personales');
  row('Nombre completo', g('f-nombre'));
  row('Fecha de nacimiento', g('f-dob'));
  row('Teléfono', g('f-tel'));
  row('Correo electrónico', g('f-email'));
  row('Cédula / ID', g('f-cedula'));
  div();

  secTitle('2. Antecedentes personales patológicos');
  block('Condiciones', cbs('pat') + (g('pat-otro') ? ' / Otro: ' + g('pat-otro') : ''));
  div();

  secTitle('3. Antecedentes personales no patológicos');
  block('Hábitos', cbs('nopat'));
  if (g('drogas-cuales')) row('Drogas (cuáles)', g('drogas-cuales'));
  if (g('nopat-obs')) block('Observaciones', g('nopat-obs'));
  div();

  secTitle('4. Anticonceptivos');
  block('Método(s)', cbs('ac') + (g('ac-cual') ? ' — ' + g('ac-cual') : ''));
  div();

  secTitle('5. Alergias');
  if (g('alerg-med')) block('Medicamentos', g('alerg-med'));
  if (g('alerg-alim')) block('Alimentos / látex', g('alerg-alim'));
  if (g('alerg-anest')) row('Reacción a anestesia', g('alerg-anest'));
  div();

  secTitle('6. Antecedentes ginecológicos');
  row('Fecha última menstruación', g('gyn-fum'));
  row('Fórmula obstétrica', `G${g('gyn-emb')||'0'}  P${g('gyn-pv')||'0'}  C${g('gyn-ces')||'0'}  A${g('gyn-ab')||'0'}`);
  row('Menopausia', g('gyn-meno'));
  if (g('gyn-obs')) block('Observaciones', g('gyn-obs'));
  div();

  secTitle('7. Antecedentes quirúrgicos — Cirugías de salud');
  if (g('qx-salud')) block('Cirugías previas', g('qx-salud'));
  if (g('qx-meds')) block('Medicamentos actuales', g('qx-meds'));
  div();

  secTitle('8. Antecedentes quirúrgicos — Cirugía plástica');
  row('Procedimiento', g('cp-proc'));
  row('Fecha aproximada', g('cp-fecha'));
  row('Médico', g('cp-medico'));
  row('Clínica / lugar', g('cp-lugar'));
  row('Satisfacción (1–5)', g('cp-sat') || '—');
  if (g('cp-obs')) block('Comentarios', g('cp-obs'));
  div();

  secTitle('9. Indicaciones importantes');
  indLine('ind1', 'Suspenderé anticonceptivos orales o inyectables mínimo 2 semanas antes de la cirugía y no los retomaré hasta después de 1 mes de recuperación.');
  indLine('ind2', 'El cigarrillo y las drogas están estrictamente prohibidos antes de la cirugía y durante toda la recuperación postoperatoria.');
  indLine('ind3', 'Suspenderé el consumo de alcohol mínimo 1 semana antes de la cirugía.');
  indLine('ind4', 'Evitaré viajes y cargas pesadas durante 1 a 2 meses después de la cirugía.');
  indLine('ind5', 'Informaré al médico si tengo algún déficit nutricional antes del procedimiento.');
  indLine('ind6', 'Entiendo que no cumplir con estas indicaciones puede ser causa de suspensión o postergación de la cirugía.');
  y += 2;

  // Declaración
  chk(22);
  doc.setFillColor(234, 245, 239);
  const dtext = 'Declaro que la información suministrada es verídica y completa. Entiendo que no seguir las indicaciones médicas puede comprometer todas las etapas de la cirugía, tanto las previas como las posteriores. Asimismo, reconozco que los presupuestos son aproximados y están sujetos a cambio según situaciones alternas que puedan presentarse.';
  const dlines = doc.splitTextToSize(dtext, CW - 6);
  doc.roundedRect(PL, y, CW, dlines.length * 4.5 + 7, 1.5, 1.5, 'F');
  doc.setFont('helvetica', 'normal'); doc.setFontSize(8.5); doc.setTextColor(21, 90, 55);
  doc.text(dlines, PL + 3, y + 5);
  y += dlines.length * 4.5 + 11;

  // Firma
  chk(50);
  secTitle('10. Firma');
  row('Nombre', g('sign-nombre'));
  row('Cédula', g('sign-cedula'));
  row('Fecha', g('sign-fecha'));
  y += 3;

  if (hasSig) {
    const sigData = canvas.toDataURL('image/png');
    chk(38);
    doc.setDrawColor(180, 190, 210); doc.setLineWidth(0.5);
    doc.rect(PL, y, 85, 32);
    doc.addImage(sigData, 'PNG', PL + 1, y + 1, 83, 30);
    doc.setFont('helvetica', 'normal'); doc.setFontSize(7.5); doc.setTextColor(150, 155, 165);
    doc.text('Firma del/la paciente', PL + 2, y + 35);
    y += 38;
  } else {
    chk(38);
    doc.setDrawColor(180, 190, 210); doc.setLineWidth(0.5);
    doc.rect(PL, y, 85, 32);
    doc.setFont('helvetica', 'normal'); doc.setFontSize(7.5); doc.setTextColor(180, 180, 190);
    doc.text('Sin firma digital capturada', PL + 3, y + 17);
    doc.text('Firma del/la paciente', PL + 2, y + 35);
    y += 38;
  }

  // Footer
  const pages = doc.internal.getNumberOfPages();
  for (let p = 1; p <= pages; p++) {
    doc.setPage(p);
    doc.setFont('helvetica', 'normal'); doc.setFontSize(7.5); doc.setTextColor(165, 165, 175);
    doc.text('Documento confidencial — Historia Clínica Cirugía Plástica', PL, 291);
    doc.text(`Página ${p} de ${pages}`, W - PR, 291, { align: 'right' });
  }

  return doc;
}

// ─── Buttons ─────────────────────────────────────────────────────
function setLoading(btnId, spinId, lblId, loading, defaultLabel) {
  const btn = document.getElementById(btnId);
  const spin = document.getElementById(spinId);
  const lbl = document.getElementById(lblId);
  btn.disabled = loading;
  spin.style.display = loading ? 'inline-block' : 'none';
  lbl.textContent = loading ? 'Generando PDF…' : defaultLabel;
}

document.getElementById('btn-download').addEventListener('click', async () => {
  setLoading('btn-download', 'spin2', 'lbl-dl', true, 'Solo descargar PDF');
  try {
    await new Promise(r => setTimeout(r, 40));
    const doc = buildPDF();
    const nombre = g('f-nombre') || 'paciente';
    doc.save(`historia_clinica_${nombre.replace(/\s+/g, '_')}.pdf`);
    showToast('PDF descargado correctamente.');
  } catch (e) {
    showToast('Error al generar el PDF: ' + e.message);
  } finally {
    setLoading('btn-download', 'spin2', 'lbl-dl', false, 'Solo descargar PDF');
  }
});

document.getElementById('btn-send').addEventListener('click', async () => {
  setLoading('btn-send', 'spin1', 'lbl-send', true, 'Generar PDF y enviar');
  try {
    await new Promise(r => setTimeout(r, 40));
    const doc = buildPDF();
    const nombre = g('f-nombre') || 'paciente';
    const filename = `historia_clinica_${nombre.replace(/\s+/g, '_')}.pdf`;
    doc.save(filename);

    await new Promise(r => setTimeout(r, 900));

    const subject = encodeURIComponent(`Historia clínica — ${nombre}`);
    const body = encodeURIComponent(
`Estimado/a doctor/a,

Le envío mi historia clínica completa adjunta como archivo PDF ("${filename}"), el cual acaba de descargarse en su dispositivo.

Datos de contacto:
  Nombre:   ${g('f-nombre') || '—'}
  Cédula:   ${g('f-cedula') || '—'}
  Teléfono: ${g('f-tel') || '—'}

Recuerde adjuntar el archivo PDF descargado antes de enviar este correo.

Saludos,
${g('sign-nombre') || nombre}`);

    window.location.href = `mailto:${DOCTOR_EMAIL}?subject=${subject}&body=${body}`;
    showToast('PDF descargado. Adjúntelo en el correo que se abrió y envíelo.', 6000);
  } catch (e) {
    showToast('Error: ' + e.message);
  } finally {
    setLoading('btn-send', 'spin1', 'lbl-send', false, 'Generar PDF y enviar');
  }
});
</script>
</body>
</html>
