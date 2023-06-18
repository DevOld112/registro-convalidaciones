# Registro de Convalidaciones
## Contexto de creacion:

Actualmente me encuentro laborando en el area administrativa de una clinica ocupacional enfocada en el area minera. Ultimamente se han estado presentando inconvenientes para llevar un control ordenado y certero sobre las convalidaciones (Cuando una empresa solicita que su paciente pase mas de un perfil medico y solicitan convalidar uno o mas de estos para reducir los costos)

El problema que habia con este procedimiento es que una de mis funciones validar estos perfiles y asignar la base en funcion del precio mayor, pero al finalizar el mes, saltaba algun fallo debido a que estos examenes no se me hacian llegar para su correcta validacion, ahora por cuenta propia he decidido crear esta aplicacion con Vue para registrar los examenes que me hace llegar el area de recepcion para yo llevar un control interno mas organizado de todo.

## Proceso de Creacion: 

Esta app fue creada con VueJS y originalmente era un registro para pacientes de una veterinaria, por lo que he decidido adaptarlo a mi necesidad.

Esta app usa 4 componentes para el renderizado: `Header`, `Formulario`, `Alerta`, `Paciente`

El formulario recibe toda la informacion que necesito para poder llevar un control organizado de todo y se guarda en el Local Storage de la computadora, por lo que no deberia haber problema tener todo organizado.

Cuando se genera un registro, esto lo hace mediante un ID, esta funcion la importe mediante `UID` de `uid`, adicional a eso se pudo realizar la funcionalidad del boton editar para que no agrege un registro adicinal con los mismos datos, un boton eliminar por si deseo anular dicho registro.

Para el apartado de estilos de este proyecto se uso Tailwindcss

Ver deployment del proyecto aqui: https://648f5ec794a8665ec3b93ac7--frabjous-cannoli-3f45df.netlify.app/
