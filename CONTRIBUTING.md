# Contribuir a CVGmini  

Primero, gracias por querer meter mano en **CVGmini**. Segundo, **esto no es un patio de juegos**, así que sigue estas reglas si no quieres que tu PR termine en la papelera más rápido de lo que tarda un `var_dump()` en romper producción.  


## ⚠️ Seguridad: No metas código inseguro o serás ignorado  

Aquí no se aceptan vulnerabilidades disfrazadas de "mejoras". No insistas.  

- **Toda entrada de usuario debe ser validada y sanitizada**.  
- **Nada de `eval()`, `exec()`, `shell_exec()`, `system()` ni tonterías similares**.  
- **Prohibido confiar en `$_GET`, `$_POST`, `$_REQUEST` sin validación estricta**.  
- **Nada de exponer errores en producción**. Si ves un `var_dump()` en el código, bórralo antes de enviar el PR.  
- **Nunca, pero NUNCA, subas credenciales o datos sensibles**. Parece obvio, pero siempre hay alguien que lo hace.  

Si tu código tiene algún agujero de seguridad, lo voy a rechazar sin siquiera mirarlo dos veces.  


## Reglas básicas para contribuir  

- **No vengas a cambiar cosas críticas sin aprobación previa.** Abre un Issue y espera respuesta antes de tocar algo importante.  
- **Código modular y reutilizable.** Si tu función parece un script de 1999, ni lo intentes.  
- **Nada de frameworks ni dependencias externas.** CVGmini es **PHP puro**. Si necesitas Laravel para hacer un `if`, este no es tu proyecto.  
- **Comenta tu código.** Pero comentarios útiles, no obviedades.  
- **Cada contribución se revisa minuciosamente.** Si algo no me convence, te lo haré cambiar.  


## Cómo comentar el código correctamente  

Los comentarios deben ser **precisos, útiles y técnicos**. Nada de explicaciones obvias ni frases innecesarias.  

### ❌ Errores comunes al comentar (NO HAGAS ESTO)  

#### Comentarios obvios e innecesarios  
```php
// Suma dos números  
$resultado = $a + $b;
```  
Este comentario no aporta nada útil. Si el código se entiende solo, **no lo comentes**.  

#### Comentarios en tono informal o en plural  
```php
// Aquí validamos si el usuario está autenticado  
if (!isset($_SESSION['usuario'])) { ... }
```  
Nada de "aquí", "validamos" o "hacemos". **El código se comenta en tercera persona, sin plurales**.  

#### Comentarios vagos o genéricos  
```php
// Validación  
if ($edad >= 18) { ... }
```  
¿Validación de qué? Explica claramente **qué se está validando y por qué**.  


### ✅ Forma correcta de comentar  

#### Usar PHPDoc en funciones y métodos  
```php
/**
 * Calcula el total con impuestos aplicados.
 *
 * @param float $monto Monto original sin impuestos.
 * @param float $impuesto Porcentaje de impuesto a aplicar.
 * @return float Total con impuestos incluidos.
 */
function calcularTotalConImpuesto(float $monto, float $impuesto): float {
    return $monto + ($monto * $impuesto / 100);
}
```  
Cada parámetro y retorno deben explicarse con claridad.  

#### Comentarios solo donde sean necesarios  
```php
// Se verifica si el usuario tiene sesión activa.
if (!isset($_SESSION['usuario'])) { 
    exit('Acceso denegado'); 
}
```  
Solo comenta **cuando el propósito del código no sea evidente a primera vista**.  

#### Explicaciones claras y técnicas, sin darle vueltas al asunto  
```php
// Se convierte la fecha a formato ISO 8601 para compatibilidad con APIs.
$fechaISO = date('c', strtotime($fecha));
```  
Se explica qué hace el código y por qué es relevante.  

#### Evitar comentarios innecesarios  
```php
$total = $precio * $cantidad; // ❌ No hace falta explicar esto
```  
Si el código es **autoexplicativo**, el comentario **sobra**.  


### ⚠️ Regla de oro  
Si un comentario **no aporta valor real**, **bórralo**. Un buen código **no necesita ser narrado**, solo aclarado cuando sea necesario.  



## 🔄 Cómo contribuir sin que tu PR sea rechazado al instante  

1. **Haz un fork** del repo en tu cuenta.  
2. **Crea una rama** con un nombre decente:  
   ```bash
   git checkout -b fix-validacion-formularios
