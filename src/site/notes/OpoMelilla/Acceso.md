---
{"dg-publish":true,"permalink":"/opo-melilla/acceso/"}
---


export async function middleware(req) {
  const auth = Buffer.from(req.headers.get("authorization") || "").toString("base64");
  const validAuth = Buffer.from("opomelilla:Prueba.01.").toString("base64"); // Cambia "usuario:contraseña" por tus credenciales

  if (auth !== validAuth) {
    return new Response("Acceso no autorizado", {
      status: 401,
      headers: {
        "WWW-Authenticate": 'Basic realm="Restricted Area"',
      },
    });
  }
  return NextResponse.next(); // Si usas Next.js, descomenta esta línea
}