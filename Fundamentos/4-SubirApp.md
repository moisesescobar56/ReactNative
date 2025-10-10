# Subir App a repositorio de Github

## Requisitos
- Git x64 instalado.
- Cuenta de GitHub.
- Conocimientos basicos de Git.

## Crear repositorio

**PASO 1:** crear respositorio en Github.

<img width="1355" height="775" alt="image" src="https://github.com/user-attachments/assets/39347a68-fb15-40df-a6a1-a1d471b6fd52" />

**PASO 2:** nombrar el repositorio y dar clic en **Crear**.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/248bef87-b7d8-48e8-969e-889dec61d103" />

**PASO 3:** copiar url del repositorio creado.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/59088217-5b25-4dc9-a358-3bc8a66d813d" />


## Subir repositorio

**PASO 1:** abrir una nueva terminal(preferencia CMD) en VS Code.

<img width="1598" height="787" alt="image" src="https://github.com/user-attachments/assets/2d5b0fdb-5bee-44d4-a76e-8ba9385c1c41" />

**Resultado:**

<img width="1599" height="785" alt="image" src="https://github.com/user-attachments/assets/e17f8ce2-9a28-44c9-888c-d79eccadbefa" />

**PASO 2:** ejecutar los siguientes comandos en la terminal.

```code
git add .
```
<img width="1598" height="785" alt="image" src="https://github.com/user-attachments/assets/dd879b9e-ee60-4c95-92cd-7b400c210052" />

```code
git commit -m "Subir app"
```

<img width="1598" height="785" alt="image" src="https://github.com/user-attachments/assets/79f42cca-4f32-467b-a4d8-4f42141dc792" />


```code
git remote add origin urlCopiada
```

<img width="1598" height="785" alt="image" src="https://github.com/user-attachments/assets/ec07c4fc-726b-4901-acda-43fc5cc449ce" />

```code
git branch -M main
```

<img width="1598" height="785" alt="image" src="https://github.com/user-attachments/assets/501855e4-a020-40c2-bf0e-cb5bdb8f4d87" />

```code
git push -u origin main
```

<img width="1598" height="785" alt="image" src="https://github.com/user-attachments/assets/355cc1b8-1a22-4470-8cf8-760131e43f39" />

**PASO 3:** autentica tu cuenta cuando hagas el `push`.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1dee4d35-d908-4813-b0f6-f660c807ef49" />

<img width="1146" height="832" alt="image" src="https://github.com/user-attachments/assets/6e85f8ca-6d79-4663-ab9e-e1d26a5d7b31" />

**Resultado:** revisa en VS Code que se hayan subido los cambios.
<img width="1598" height="785" alt="image" src="https://github.com/user-attachments/assets/cb2a7220-2a18-4a7a-8ac8-7b42dec91716" />

**PASO 4:** actualizar la pagina de Github para confirmar que se subieron los cambios.

<img width="1355" height="775" alt="image" src="https://github.com/user-attachments/assets/d4697392-0ff4-4d7e-bf17-fb44e1a5371b" />

**Resultado:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a790f7ca-29ed-4708-b16d-71da4b5ca254" />

