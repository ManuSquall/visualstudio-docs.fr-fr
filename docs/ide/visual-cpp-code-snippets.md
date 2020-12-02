---
title: Extraits de code Visual C++
description: Découvrez comment utiliser des extraits de code pour ajouter du code couramment utilisé à vos fichiers de code C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: corob-msft
ms.author: corob
manager: markl
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: e5cde2be817c49344e02ff06030022f99790a7a2
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478807"
---
# <a name="visual-c-code-snippets"></a>Extraits de code Visual C++

Dans Visual Studio, vous pouvez utiliser des extraits de code pour ajouter du code couramment utilisé dans vos fichiers de code C++. En général, vous pouvez utiliser les extraits de code quasiment de la même façon que dans C#, mais l'ensemble d'extraits de code par défaut est différent.

Vous pouvez ajouter un extrait de code à un emplacement particulier dans votre code (insertion) ou sélectionner du code pour l'entourer d'un extrait de code.

## <a name="insert-a-code-snippet"></a>Insérer un extrait de code

Pour insérer un extrait de code, ouvrez un fichier de code C++ (*. cpp* ou *. h*), cliquez n’importe où dans le fichier et effectuez l’une des opérations suivantes :

- Effectuez un clic droit pour afficher le menu contextuel et sélectionnez **Insérer un extrait**

- Dans le menu **Edition / IntelliSense**, sélectionnez **Insérer un extrait**

- Utilisez les raccourcis clavier : **CTRL** + **K** + **X**

Vous devez voir une liste de choix commençant par **#if**. Quand vous sélectionnez **#if**, vous devez voir le code suivant ajouté au fichier :

```cpp
#if 0

#endif // 0
```

Vous pouvez alors remplacer le **0** par la condition correcte.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Utiliser un extrait de code pour entourer du code sélectionné

Pour utiliser un extrait de code pour entourer du code sélectionné, sélectionnez une ligne (ou plusieurs lignes) et effectuez l'une des opérations suivantes :

- Cliquez avec le bouton droit pour afficher le menu contextuel, puis sélectionnez **entourer de**

- Dans le menu **modifier**  >  **IntelliSense** , sélectionnez **entourer de**

- À l’aide d’un clavier, appuyez sur **CTRL** + **K** + **S** .

Sélectionnez **#if**. Un résultat semblable à celui-ci doit s’afficher :

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

Vous pouvez alors remplacer le 0 par la condition correcte.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Où puis-je trouver la liste complète des extraits de code C++ ?

Vous pouvez trouver la liste complète des extraits de code C++ en accédant au **Gestionnaire des extraits de code** (dans le menu **Outils**) et en définissant le **langage** sur **Visual C++**. Dans la fenêtre ci-dessous, développez **Visual C++**. Vous devez voir les noms de tous les extraits de code C++ dans l'ordre alphabétique.

Les noms de la plupart des extraits de code sont explicites, mais certains noms peuvent prêter à confusion.

## <a name="class-vs-classi"></a>Comparaison de class et classi

L’extrait de code **class** fournit la définition d’une classe nommée `MyClass`, avec le constructeur et le destructeur par défaut appropriés, et pour laquelle les définitions du constructeur et du destructeur se trouvent en dehors de la classe :

```cpp
class MyClass
{
public:
    MyClass();
    ~MyClass();

private:

};

MyClass::MyClass()
{
}

MyClass::~MyClass()
{
}
```

L’extrait de code **classi** fournit également la définition d’une classe nommée `MyClass`, mais le constructeur et le destructeur par défaut sont définis à l’intérieur de la définition de la classe :

```cpp
class MyClass
{
public:
    MyClass()
    {
    }

    ~MyClass()
    {
    }

private:

};
```

## <a name="for-vs-forr-vs-rfor"></a>Comparaison de for, forr et rfor

Il existe trois extraits de code **for** différents qui fournissent des types différents de boucles `for`.

L’extrait de code **rfor** fournit une boucle for [basée sur une plage](/cpp/cpp/range-based-for-statement-cpp) (lien). Cette construction est préférable aux boucles `for` basées sur un index.

```cpp
for (auto& i : v)
{

}
```

L’extrait **de code for** fournit une `for` boucle dans laquelle la condition est basée sur la longueur (en `size_t` ) d’un objet.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

L’extrait de code **forr** fournit une `for` boucle inverse dans laquelle la condition est basée sur la longueur (en entiers) d’un objet.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>Extrait de code du destructeur (~)

L’extrait de code du destructeur ( **~** ) présente un comportement différent dans des contextes différents. Si vous insérez cet extrait dans une classe, il fournit un destructeur pour cette classe. Examinons, par exemple, le code suivant :

```cpp
class SomeClass {

};
```

Si vous insérez l’extrait de code du destructeur, il fournit un destructeur pour `SomeClass` :

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

Si vous essayez d'insérer l'extrait de code destructeur en dehors d'une classe, il fournit un destructeur avec un nom d'espace réservé :

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>Voir aussi

- [Extraits de code](../ide/code-snippets.md)