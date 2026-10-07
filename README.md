# gresp-2026
Página de conferência dos resultados das Eleições do GRESP 2026-2027
<!doctype html>
<html lang="pt-BR">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Conferência do Resultado - GRESP 2026</title>
<style>
:root{--azul:#17365d;--azul2:#2878d0;--verde:#18835a;--roxo:#7048a8;--laranja:#e67e22;--claro:#f3f6f8;--linha:#cbd5df;--vermelho:#b42318;--texto:#243444}
*{box-sizing:border-box} body{margin:0;background:#eef3f7;color:var(--texto);font:15px Arial,sans-serif}
header{background:linear-gradient(135deg,#17365d,#2878d0);color:#fff;padding:24px 18px;text-align:center}
header h1{margin:0;font-size:28px} header p{margin:7px 0 0}.wrap{max-width:1180px;margin:20px auto;padding:0 14px}
.alerta{background:#fff7e6;border-left:5px solid var(--laranja);padding:12px 15px;border-radius:8px;margin-bottom:16px}
.grid{display:grid;grid-template-columns:1fr 1fr;gap:16px}.card{background:#fff;border-radius:14px;box-shadow:0 4px 16px #17365d18;padding:18px}.card h2{margin:0 0 13px;color:var(--azul)}
.meta{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:14px}label{display:block;font-weight:700;font-size:12px;color:#526273}input{width:100%;border:1px solid var(--linha);border-radius:7px;padding:9px;margin-top:4px;font-size:15px}input[type=number]{text-align:center;color:#004dc1;font-weight:700}
table{width:100%;border-collapse:collapse}th{background:var(--azul);color:#fff;padding:9px 6px;font-size:12px}td{border-bottom:1px solid #e5ebf0;padding:7px 5px}td.num{text-align:center;font-weight:700;width:54px}td.voto{width:92px}.total{font-weight:700;background:var(--claro)}
.status{padding:10px;border-radius:8px;margin-top:12px;font-weight:700;text-align:center}.ok{background:#e8f6ef;color:#126641}.erro{background:#fdecec;color:var(--vermelho)}
.resumo{margin-top:16px}.resumo-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:10px}.kpi{background:var(--claro);padding:14px;border-radius:10px;text-align:center}.kpi b{display:block;font-size:22px;color:var(--azul)}
.ranking{margin-top:15px}.bar{height:18px;background:#e6edf3;border-radius:9px;overflow:hidden}.fill{height:100%;background:linear-gradient(90deg,var(--azul2),var(--roxo))}.champ{background:#e8f6ef!important;color:#126641;font-weight:700}
.acoes{display:flex;gap:10px;flex-wrap:wrap;margin:16px 0}button{border:0;border-radius:8px;padding:11px 16px;font-weight:700;cursor:pointer}button.primary{background:var(--azul);color:#fff}button.secondary{background:#fff;color:var(--azul);border:1px solid var(--azul)}button.danger{background:#fff0f0;color:var(--vermelho);border:1px solid #efc2c2}
footer{text-align:center;color:#637382;padding:25px}.print-only{display:none}
@media(max-width:800px){.grid{grid-template-columns:1fr}.resumo-grid{grid-template-columns:1fr 1fr}}
@media print{body{background:#fff;font-size:11px}header{padding:12px;-webkit-print-color-adjust:exact;print-color-adjust:exact}.wrap{max-width:none;margin:5px}.card{box-shadow:none;border:1px solid #aaa;padding:10px}.acoes,.alerta{display:none}.grid{gap:8px}.print-only{display:block}.resumo-grid{grid-template-columns:repeat(4,1fr)}input{border:0;padding:2px}.status{border:1px solid #aaa}.page-break{break-before:page}}
</style>
</head>
<body>
<header><h1>Conferência do Resultado - GRESP 2026</h1><p>EE Abílio Raposo Ferraz Júnior | Zona 903ª | Votação eletrônica | 8 de outubro de 2026</p></header>
<div class="wrap">
<div class="alerta"><b>Uso exclusivo para conferência.</b> Transcreva os resultados dos relatórios eletrônicos das urnas. Este site não substitui os documentos oficiais, as atas nem a planilha de apuração.</div>
<div class="acoes"><button class="primary" onclick="salvar()">Salvar neste dispositivo</button><button class="secondary" onclick="window.print()">Imprimir / Salvar em PDF</button><button class="danger" onclick="limparTudo()">Limpar dados</button></div>
<div class="grid" id="urnas"></div>
<div class="card resumo page-break">
<h2>Resultado consolidado</h2>
<div class="resumo-grid">
<div class="kpi">Eleitores aptos<b id="aptosG">746</b></div><div class="kpi">Votantes<b id="votantesG">0</b></div><div class="kpi">Votos válidos<b id="validosG">0</b></div><div class="kpi">Comparecimento<b id="compG">0,0%</b></div>
</div>
<div class="ranking"><table><thead><tr><th>Nº</th><th>Chapa</th><th>Urna 1</th><th>Urna 2</th><th>Total</th><th>% válidos</th><th>Classificação</th></tr></thead><tbody id="ranking"></tbody></table></div>
<div id="resultadoFinal" class="status"></div>
<div class="print-only"><p><b>Conferido por:</b> __________________________________________ &nbsp; <b>Data:</b> ____/____/2026</p></div>
</div>
</div>
<footer>Edital nº 001/2026 | Planilha oficial: PLANILHA_DE_APURACAO_GRESP_2026_9_CHAPAS_CORRIGIDA.xlsx</footer>
<script>
const chapas=[['10','FIFA STREET'],['17','CONSCIENTIZAÇÃO DA ESCOLA'],['55','ESPORTES FC'],['67','CHAPA DA TODDY'],['77','VOZES DO ABÍLIO'],['90','JOVENS GREMISTAS'],['95','RELÂMPAGO ABÍLIO'],['97','UNIDOS PELO FUTURO'],['99','ABÍLIO TRANSFORMA']];
const urnas=[{id:1,nome:'Urna 1 - 1ª Seção',aptos:359,cor:'#2878d0'},{id:2,nome:'Urna 2 - 2ª Seção',aptos:387,cor:'#7048a8'}];
function n(v){return Number(v)||0} function pct(a,b){return b?((a/b)*100).toFixed(1).replace('.',',')+'%':'0,0%'}
function montar(){document.getElementById('urnas').innerHTML=urnas.map(u=>`<section class="card" style="border-top:6px solid ${u.cor}"><h2>${u.nome}</h2><div class="meta"><label>Eleitores aptos<input value="${u.aptos}" disabled></label><label>Comparecimento<input id="comparecimento${u.id}" type="number" min="0" max="${u.aptos}" oninput="calcular()"></label><label>Horário de abertura<input id="abertura${u.id}" type="time"></label><label>Horário de encerramento<input id="encerramento${u.id}" type="time"></label></div><table><thead><tr><th>Nº</th><th>Chapa</th><th>Votos</th></tr></thead><tbody>${chapas.map(c=>`<tr><td class="num">${c[0]}</td><td>${c[1]}</td><td class="voto"><input id="u${u.id}c${c[0]}" type="number" min="0" value="0" oninput="calcular()"></td></tr>`).join('')}<tr class="total"><td colspan="2">Votos válidos</td><td id="validos${u.id}">0</td></tr><tr><td colspan="2">Votos em branco</td><td><input id="brancos${u.id}" type="number" min="0" value="0" oninput="calcular()"></td></tr><tr><td colspan="2">Votos nulos</td><td><input id="nulos${u.id}" type="number" min="0" value="0" oninput="calcular()"></td></tr><tr class="total"><td colspan="2">Total de votos registrados</td><td id="total${u.id}">0</td></tr><tr class="total"><td colspan="2">Ausentes</td><td id="ausentes${u.id}">${u.aptos}</td></tr></tbody></table><div id="status${u.id}" class="status"></div></section>`).join(''); carregar(); calcular()}
function calcular(){let totais={};chapas.forEach(c=>totais[c[0]]={nome:c[1],u1:0,u2:0,total:0});let votantesG=0,validosG=0;urnas.forEach(u=>{let validos=0;chapas.forEach(c=>{let v=n(document.getElementById(`u${u.id}c${c[0]}`).value);validos+=v;totais[c[0]][`u${u.id}`]=v;totais[c[0]].total+=v});let br=n(document.getElementById('brancos'+u.id).value),nu=n(document.getElementById('nulos'+u.id).value),total=validos+br+nu,comp=n(document.getElementById('comparecimento'+u.id).value);document.getElementById('validos'+u.id).textContent=validos;document.getElementById('total'+u.id).textContent=total;document.getElementById('ausentes'+u.id).textContent=Math.max(0,u.aptos-comp);let st=document.getElementById('status'+u.id);if(comp===total){st.className='status ok';st.textContent='CONFERÊNCIA OK: comparecimento igual ao total de votos.'}else{st.className='status erro';st.textContent=`DIVERGÊNCIA: comparecimento ${comp} e votos ${total}. Diferença: ${comp-total}.`}votantesG+=comp;validosG+=validos});
let arr=Object.entries(totais).sort((a,b)=>b[1].total-a[1].total);document.getElementById('ranking').innerHTML=arr.map(([num,x],i)=>`<tr class="${i===0?'champ':''}"><td class="num">${num}</td><td>${x.nome}</td><td class="num">${x.u1}</td><td class="num">${x.u2}</td><td class="num">${x.total}</td><td class="num">${pct(x.total,validosG)}</td><td class="num">${i+1}º</td></tr>`).join('');document.getElementById('votantesG').textContent=votantesG;document.getElementById('validosG').textContent=validosG;document.getElementById('compG').textContent=pct(votantesG,746);let rf=document.getElementById('resultadoFinal');if(validosG===0){rf.className='status';rf.textContent='Aguardando lançamento dos resultados.'}else if(arr.length>1&&arr[0][1].total===arr[1][1].total){rf.className='status erro';rf.textContent='EMPATE NA PRIMEIRA COLOCAÇÃO: conferir o regulamento e deliberar.'}else{rf.className='status ok';rf.textContent=`CHAPA MAIS VOTADA: ${arr[0][0]} - ${arr[0][1].nome}, com ${arr[0][1].total} votos (${pct(arr[0][1].total,validosG)} dos válidos). Conferir a regra de maioria e eventual segundo turno no Edital nº 001/2026.`}}
function campos(){return [...document.querySelectorAll('input:not([disabled])')]}function salvar(){let d={};campos().forEach(x=>d[x.id]=x.value);localStorage.setItem('gresp_apuracao_2026',JSON.stringify(d));alert('Dados salvos neste dispositivo.')}function carregar(){let d=JSON.parse(localStorage.getItem('gresp_apuracao_2026')||'{}');campos().forEach(x=>{if(d[x.id]!==undefined)x.value=d[x.id]})}function limparTudo(){if(confirm('Deseja apagar todos os dados lançados neste dispositivo?')){localStorage.removeItem('gresp_apuracao_2026');location.reload()}}
montar();
</script>
</body></html>
