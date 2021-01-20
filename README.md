<a href="https://desarrolladores.addonpayments.com/" target="_blank">
    <img src="https://desarrolladores.addonpayments.com/assets/images/branding/comercia/logo.svg?v=?v=1.14.1" alt="Addon Payments logo" title="Addon Payments" align="right" width="225" />
</a>

# SDK de Javascript Comercia Global Payments

Este SDK ha sido adaptado por Comercia Global Payments.

## Biblioteca JS de la página de pago alojado (HPP)

### Uso

Este código solo debe ejecutarse cuando el DOM está completamente cargado.

```javascript
RealexHpp.init(payButtonId, merchantUrl, jsonFromServerSdk);
```

- payButtonId: ID del botón utilizado para iniciar el Lightbox.
- merchantUrl: URL en la que se publicará la respuesta JSON de Addon Payments.
- jsonFromServerSdk: Respuesta JSON del servidor de Addon Payments.

En la documentación de cada SDK [(PHP, JAVA, .NET)](https://github.com/addonpayments), podrá comprobar que usamos el siguiente código:

```javascript
$(document).ready(function () {
  $.getJSON("request.php", function (jsonFromRequestEndpoint) {
    RealexHpp.setHppUrl("https://hpp.sandbox.addonpayments.com/pay");
    RealexHpp.lightbox.init(
      "payButtonId",
      "https://midominio.es/response.php",
      jsonFromRequestEndpoint
    );
  });
});
```

### Debug

Para utilizar la función de Debug y ver los errores por consola, debe indicar el siguiente parámetro en sus peticiones mediante HPP.

```javascript
RealexHpp.setDebugErrors(true);
```

Quedando el código de la siguiente forma:

```javascript
$(document).ready(function () {
  $.getJSON("request.php", function (jsonFromRequestEndpoint) {
    RealexHpp.setHppUrl("https://hpp.sandbox.addonpayments.com/pay");
    RealexHpp.setDebugErrors(true);
    RealexHpp.lightbox.init(
      "payButtonId",
      "https://midominio.es/response.php",
      jsonFromRequestEndpoint
    );
  });
});
```

### Consumiendo la petición POST

Una vez que se haya completado el pago, la respuesta de JSON se publicará en la merchantUrl indicada. El nombre del campo que contiene la respuesta JSON es hppResponse.

## Biblioteca remota de JS

### Funciones de validación

- validateCardNumber: valida el formato del número de tarjeta y realiza una verificación Luhn
- validateCardHolderName: valida que el nombre del titular de la tarjeta está compuesto por caracteres ISO / IEC 8859-1: 1998
- validateCvn: ​​valida CVN no Amex
- validateAmexCvn: ​​valida Amex CVN
- validateExpiryDateFormat: valida el formato de fecha de vencimiento
- validateExpiryDateNotInPast: valida que la fecha de caducidad no está pasada

### Uso

```javascript
RealexRemote.validateCardNumber(cardNumber);
RealexRemote.validateCardHolderName(cardHolderName);
RealexRemote.validateCvn(cvn);
RealexRemote.validateAmexCvn(amexCvn);
RealexRemote.validateExpiryDateFormat(expiryDate);
RealexRemote.validateExpiryDateNotInPast(expiryDate);
```

#### Datos de tarjeta de prueba

| Nombre      | Número           | Exp Mes | Exp Año | CVN  |
| ----------- | ---------------- | ------- | ------- | ---- |
| Visa        | 4263970000005262 | 12      | 2025    | 123  |
| MasterCard  | 2223000010005780 | 12      | 2019    | 900  |
| MasterCard  | 5425230000004415 | 12      | 2025    | 123  |
| Discover    | 6011000000000087 | 12      | 2025    | 123  |
| Amex        | 374101000000608  | 12      | 2025    | 1234 |
| JCB         | 3566000000000000 | 12      | 2025    | 123  |
| Diners Club | 36256000000725   | 12      | 2025    | 123  |

## Soporte

En caso de que quiera hablar con un especialista de Addon Payments, deberá llamar al teléfono [914 353 028](tel:914353028) o enviar un email a [soporte@addonpayments.com](mailto:soporte@addonpayments.com).

## Contribuyendo

¡Todo nuestro código es de código abierto y animamos a otros desarrolladores a contribuir y ayudar a mejorarlo!

1. Fork it
2. Cree su rama de características (`git checkout -b mi-nueva-feature`)
3. Asegúrese de que las pruebas de SDK son correctas
4. Confirme sus cambios (`git commit -am 'Añadir un commit'`)
5. Empujar a la rama (`git push origin mi-nueva-feature`)
6. Crear una nueva solicitud de extracción

## Licencia

Este proyecto está licenciado bajo la licencia MIT. Consulte el archivo ["LICENSE"](https://github.com/AddonPayments/js-sdk/blob/master/LICENSE) ubicado en la raíz del proyecto para obtener más detalles.
