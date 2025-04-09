En PHP, on utilise un **callable** pour appeler une fonction (ou une méthode) lorsque l'on veut passer une référence à cette fonction comme argument, ou lorsque l'on veut stocker cette référence dans une variable pour une exécution ultérieure. Voici les cas d'usage les plus courants :

---

### **1. Passage d'une fonction comme argument (callback)**

Beaucoup de fonctions PHP acceptent un **callable** en paramètre pour exécuter du code personnalisé. Exemples :

#### **a) Fonctions de tableau (`array_map`, `array_filter`, `usort`, etc.)**
```PHP
// Utilisation de array_map avec une fonction anonyme (callable)
$nombres = [1, 2, 3];
$carres = array_map(function($x) { return $x * $x; }, $nombres);
print_r($carres); // [1, 4, 9]

// Avec une fonction nommée (callable sous forme de string)
function double($x) { return $x * 2; }
$doubles = array_map('double', $nombres);
print_r($doubles); // [2, 4, 6]
```



#### **b) Fonctions de gestion d'événements ou hooks (ex: `call_user_func`)**
```PHP
function afficherMessage($message) {
    echo "Message : $message";
}

// Appel dynamique via callable
call_user_func('afficherMessage', 'Bonjour !'); // Affiche "Message : Bonjour !"
```



---

### **2. Stockage d'une fonction dans une variable pour appel différé**
```PHP
// Stockage d'une fonction dans une variable
$operation = function($a, $b) { return $a + $b; };
echo $operation(3, 5); // 8

// Changement dynamique de comportement
if ($condition) {
    $operation = fn($a, $b) => $a * $b; // Arrow function (PHP 7.4+)
} else {
    $operation = fn($a, $b) => $a - $b;
}
echo $operation(4, 2); // 8 (si true) ou 2 (si false)
```



---

### **3. Appel de méthodes d'objets (callable sous forme de tableau)**
```PHP
class Calculatrice {
    public function addition($a, $b) { return $a + $b; }
    public static function multiplication($a, $b) { return $a * $b; }
}

$calc = new Calculatrice();

// Appel d'une méthode d'instance
$callable = [$calc, 'addition'];
echo $callable(2, 3); // 5

// Appel d'une méthode statique
$callableStatic = ['Calculatrice', 'multiplication'];
echo $callableStatic(2, 3); // 6

// Alternative avec syntaxe "ClassName::method" (PHP 8.1+)
$callableStatic = 'Calculatrice::multiplication';
echo call_user_func($callableStatic, 2, 3); // 6

class Calculatrice {
    public function addition($a, $b) { return $a + $b; }
    public static function multiplication($a, $b) { return $a * $b; }
}

$calc = new Calculatrice();

// Appel d'une méthode d'instance
$callable = [$calc, 'addition'];
echo $callable(2, 3); // 5

// Appel d'une méthode statique
$callableStatic = ['Calculatrice', 'multiplication'];
echo $callableStatic(2, 3); // 6

// Alternative avec syntaxe "ClassName::method" (PHP 8.1+)
$callableStatic = 'Calculatrice::multiplication';
echo call_user_func($callableStatic, 2, 3); // 6
```



---

### **4. Utilisation avec `__invoke()` (objets appelables)**

Si un objet implémente `__invoke()`, il peut être utilisé comme callable :
```PHP
class Multiplicateur {
    public function __invoke($a, $b) { return $a * $b; }
}

$mult = new Multiplicateur();
echo $mult(3, 4); // 12 (via __invoke)
echo call_user_func($mult, 3, 4); // 12 (via callable)
```



---

### **5. Validation avec `is_callable()`**

Avant d'appeler un callable, il est prudent de vérifier qu'il est valide :
```PHP
$callable = 'une_fonction_inexistante';
if (is_callable($callable)) {
    call_user_func($callable);
} else {
    echo "Erreur : Callable invalide !";
}
```

---

### **Quand choisir un callable ?**

- Pour **déléguer un comportement personnalisé** (ex: tri personnalisé avec `usort`).
    
- Pour **implémenter des hooks ou des événements** (ex: systèmes de plugins).
    
- Pour **stocker dynamiquement une fonction/méthode** dans une variable.
    
- Pour **utiliser des fonctions de haut niveau** (`array_map`, `preg_replace_callback`, etc.).
    

---

### **Exemple complet avec callback personnalisé**
```PHP
function traiterDonnees(array $data, callable $callback) {
    foreach ($data as $key => $value) {
        $data[$key] = $callback($value);
    }
    return $data;
}

// Utilisation avec une fonction anonyme
$resultat = traiterDonnees([1, 2, 3], function($x) { return $x * 10; });
print_r($resultat); // [10, 20, 30]
```


---

### **Résumé**

|Cas d'utilisation|Exemple|
|---|---|
|Callback dans une fonction|`array_map(fn($x) => $x*2, [1,2,3])`|
|Méthode d'objet appelable|`$callable = [$obj, 'methode']`|
|Fonction stockée dans une variable|`$fn = 'strtoupper'; $fn('hello')`|
|Objet invocable (`__invoke`)|`$obj();` (si `__invoke` existe)|

En résumé, on utilise un **callable** dès qu'on a besoin de **flexibilité** dans l'appel de fonctions ou de méthodes, en particulier pour des architectures modulaires (callbacks, événements, etc.).