# Ejercicio 4: GitOps AppSec Pipeline

## Intro
Bienvenidxs! Este es el cuarto ejercicio del módulo de DevSecOps de Ekoparty Hackademy. En el ejercicio anterior aprendieron cómo deployar IaC bajo un enfoque de trabajo GitOps básico. En esta oportunidad profundizaremos en el uso de GitHub Actions para crear AppSec pipelines también bajo un enfoque GitOps.

## Requisitos
* Instalar git en tu entorno local - [instructivo](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Instalaci%C3%B3n-de-Git)
* Tener una cuenta en GitHub - [Sign Up](https://github.com/join)
* Implementar una instancia de [DefectDojo](https://www.defectdojo.org/) en tu entorno local utilizando alguna de alternativas oficiales [Docker Compose](https://github.com/DefectDojo/django-DefectDojo#quick-start)(recomendado), [instalación local con godojo](https://github.com/DefectDojo/godojo) y [K8s con Helm charts](https://github.com/DefectDojo/django-DefectDojo/blob/master/KUBERNETES.md)
* [opcional] Instalar [Ngrok](https://ngrok.com/download) un servicio para tunelizar conexiones hacia recursos privados desde internet, en este caso útil para exponer su instancia de DefectDojo hacia internet, de manera de poder ser consumida por el pipeline de Github Actions. (WARNING: exponer recursos a internet sin la debida hardenización puede ser riesgoso, se recomienda precaución y uso limitado a pruebas/laboratorio temporal). Si tienes un servidor o instancia con exposición a internet donde puedas hostear DefectDojo, también es válido como opción y no necesitas Ngrok (es la opción que se usa en el video a continuación).

## Recursos

En [este video](https://www.youtube.com/watch?v=iQRIHINefTo) se explica  cómo utilizar GHA para crear un AppSec pipeline utilizando una applicación Django de ejemplo y diferentes herramientas para correr lint checks, test unitarios y SAST, posteando luego los resultados en DefectDojo para seguimiento y métricas.

En el presente repositorio se encuentran los mismos recursos utilizados en el video, ¡puedes copiarlos y crear tu propio repositorio para reproducir el ejercicio!

### Para tener en cuenta:

* Deberías cambiar la URL de DefectDojo en [esta línea](https://github.com/celagus/gitops-exercise-2/blob/master/.github/workflows/gitsecops-pipeline.yml#L32) del pipeline para hacer funcionar la integración con tu propia instancia.
* Deberías crear el secreto DDOJO_TOKEN (el API token del usuario en cuestión en tu instancia de DefectDojo) - [cómo crear secretos en Github](https://docs.github.com/es/actions/reference/encrypted-secrets#creating-encrypted-secrets-for-an-environment)
* Nótese en [esta línea](https://github.com/celagus/gha-ci-test/blob/main/.github/workflows/gitsecops-pipeline.yml#L55) que el script toma como parámetro "-e" un ID de engagement de DefectDojo, este ID debe ser especificado por ti, puedes leer más sobre como generar un engagement a través de esta sencilla [documentación del proyecto](https://defectdojo.readthedocs.io/en/latest/start-using.html#create-a-new-engagement)


## Créditos
Gracias a @gothinkster, aproveché su proyecto como ejemplo! https://github.com/gothinkster/django-realworld-example-app




