---
title: Mis planes para esta web II
date: 2020-07-18
type: blog
position: dreamer
---


En "Mis planes para esta web"[^planes] escribí sobre mi visión y sobre lo que quiero conseguir con este sitio.

[^planes]: [[mis-planes-para-esta-web]] Mis planes para esta web

He estado investigando las maneras de crear una plataforma educativa puramente en HTML y estas son las opciones que he encontrado:

1. Usar una librería javascript (svelte[^svelte], angular, vue, etc...)
2. Usar una plataforma especializada en habilitar membersías en sitios estáticos

[^svelte]: https://github.com/beyonk-adventures/sapper-rbac


### Opción 1: Yo me lo guiso, yo me lo como

Ventajas: 

1. Aprender javascript entra en mis planes y que mejor que un proyecto como este para empezar
2. Las competencias que tendría que adquirir (procesar pagos, firebase, ...) me servirían para el resto de mi carrera
3. Solución 100% a medida, cero funcionalidades innecesarias
4. Los usuarios serían míos y no estarían en una base de datos de un tercero (con lo que evitamos problemas de privacidad)
5. Solución prácticamente gratis. Inversión de cero euros y cargas que se adaptan progresivamente al uso de la base de datos (firebase)

Desventajas

- Tendría que desarollar todo desde cero
- No tendría asitencia técnica, lo cual es importante en el procesamiento de pagos

Un ejemplo de páginas que usan este método es [Fireship](https://fireship.io)[^fireshipgh], que además usa [Hugo](https://gohugo.com)

[^fireshipgh]: [Github del proyecto](github.cm/fireship-io/fireship.io)

### Opción 2: 

Ventajas

1. Sitio completamente funcional desde el minuto cero
2. Fácil implementación de funcionalidades complejas:
    1. Autenticación
    2. Protección de contenidos
    3. Proceso de pagos
    4. Cupones de descuento
    5. Periodos de prueba
    6. Programa de afiliados


Desventajas:

- Al usar una plataforma de un tercero estaría a merced de sus cambios de políticas.
- ¿Privacidad de los usuarios potencialmente comprometida?
- Control limitado sobre la implementación (interfaz y experiencia de usuario)
- Pago mensual + comisión (hubiera preferido un modelo únicamente de comisiones para empezar con una inversión de cero euros)

Algunas plataformas que proponen este servicio son:

- [Memberstack](https://meberstack.io)
- [Memberspace](https://www.memberspace.com/)
- [Userbase](https://userbase.com/pricing/) [^userbase]

[^userbase]: Userbase tiene la ventaja de ser opensource

### Conclusión

Todavía no he determinado que opción voy a usar.

Por el momento, mientras estudio en paralelo el código de [Fireship](https://fireship.io), voy a crear una implementación básica con [Memberstack](https://memberstack.io) para probar la plataforma y explorar las posibilidades.

Tomaré mi decisión en función de si la plataforma se adapta o no a mis necesidades.

En cualquiera de los casos tendré que alojar mis vídeos en algún lugar. 
Por el momento, he identificado los dos siguientes servicios:

- [DTube](https://d.tube/)
- [Vimeo](https://vimeo.com)
