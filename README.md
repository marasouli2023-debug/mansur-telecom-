<!DOCTYPE html>
<html lang="ps" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>منصور ټیلیکام</title>
<style>
body{font-family:Arial;background:#f1f8f3;margin:0;color:#17452d}
header{background:#087b43;color:white;text-align:center;padding:25px}
main{max-width:600px;margin:20px auto;padding:15px}
.card{background:white;padding:20px;border-radius:14px;margin-bottom:15px}
button{background:#087b43;color:white;border:0;padding:13px 20px;border-radius:9px;font-size:16px}
#status{margin-top:15px;direction:rtl}
</style>
</head>
<body>
<header>
<h1>منصور ټیلیکام</h1>
<p>ستاسو د ډیجیټل خدمتونو مرکز</p>
</header>
<main>
<div class="card">
<h3>د Supabase اتصال</h3>
<p>د ډیټابېس د اتصال د ازموینې لپاره تڼۍ کېکاږئ.</p>
<button onclick="testConnection()">د اتصال ازموینه</button>
<p id="status">لا تر اوسه ازموینه نه ده شوې.</p>
</div>
</main>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
<script>
const SUPABASE_URL = "https://efbagnmfbtezgadduvlp.supabase.co";
const SUPABASE_KEY = "sb_publishable_avc7UzZz9WdhcKS_yePGHw_Ic3J_Yr1";

const db = window.supabase.createClient(
  SUPABASE_URL,
  SUPABASE_KEY
);

async function testConnection(){
  const status = document.getElementById("status");
  status.textContent = "د اتصال ازموینه روانه ده...";

  const {data, error} = await db
    .from("currencies")
    .select("code,name")
    .limit(5);

  if(error){
    status.textContent = "ځواب: " + error.message;
  }else{
    status.textContent = "اتصال بریالی شو! د اسعارو شمېر: " + data.length;
  }
}
</script>
</body>
</html> 
