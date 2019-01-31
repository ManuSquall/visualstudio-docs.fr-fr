---
title: Extraits de code Visual C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 74e26fd4-e5ca-4611-a816-0a521b4947a0
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cd24ef7e852d84d3213e024e53e325c0ba1d59fb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54762077"
---
# <a name="visual-c-code-snippets"></a>Extraits de code Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez utiliser des extraits de code pour ajouter du code couramment utilisé dans vos fichiers de code C++. En général, vous pouvez utiliser les extraits de code quasiment de la même façon que dans C#, mais l'ensemble d'extraits de code par défaut est différent.  
  
 Vous pouvez ajouter un extrait de code à un emplacement particulier dans votre code (insertion) ou sélectionner du code pour l'entourer d'un extrait de code.  
  
## <a name="inserting-a-code-snippet"></a>Insertion d'un extrait de code  
 Pour insérer un extrait de code, ouvrez un fichier de code C++ (.cpp ou .h), cliquez n'importe où dans le fichier et effectuez l'une des opérations suivantes :  
  
- Effectuez un clic droit pour afficher le menu contextuel et sélectionnez **Insérer un extrait**  
  
- Dans le menu **Edition / IntelliSense**, sélectionnez **Insérer un extrait**  
  
- Utilisez les touches de raccourci : **CTRL + K + X**  
  
  Vous devez voir une liste de choix commençant par **#if**. Quand vous sélectionnez **#if**, vous devez voir le code suivant ajouté au fichier :  
  
```cpp  
#if 0  
  
#endif // 0  
```  
  
 Vous pouvez alors remplacer le 0 par la condition correcte.  
  
## <a name="using-a-code-snippet-to-surround-selected-code"></a>Utilisation d'un extrait de code pour entourer du code sélectionné  
 Pour utiliser un extrait de code pour entourer du code sélectionné, sélectionnez une ligne (ou plusieurs lignes) et effectuez l'une des opérations suivantes :  
  
1. Effectuez un clic droit pour afficher le menu contextuel et sélectionnez **Entourer de**  
  
2. Dans le menu **Edition / IntelliSense**, sélectionnez **Entourer de**  
  
3. Utilisez les touches de raccourci : **CTRL + K + S**  
  
   Sélectionnez **#if**. Vous devez voir quelque chose de similaire à :  
  
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
 L’extrait de code **class** fournit la définition d’une classe nommée MyClass, avec le constructeur et le destructeur par défaut appropriés, et pour laquelle les définitions du constructeur et du destructeur sont situées en dehors de la classe :  
  
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
  
 L'extrait de code classi fournit également la définition d'une classe nommée MyClass, mais le constructeur et le destructeur par défaut sont définis à l'intérieur de la définition de la classe :  
  
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
  
## <a name="for-vs-foreach-vs-forr-vs-rfor"></a>Comparaison de for, foreach, forr et rfor  
 Il existe quatre extraits de code for différents qui fournissent des types différents de boucles for.  
  
 L’extrait **for** fournit une boucle `for` dans laquelle la condition est basée sur la longueur (en `size_t`) d’un objet :  
  
```cpp  
for (size_t i = 0; i < length; i++)  
{  
  
}  
```  
  
 L’extrait **foreach** fournit une boucle `for each` qui effectue des itérations sur les membres d’une collection :  
  
```cpp  
for each (object var in collection_to_loop)  
{  
  
}  
```  
  
 L’extrait **forr** fournit une boucle `for` inverse dans laquelle la condition est basée sur la longueur (en entiers) d’un objet :  
  
```cpp  
for (int i = length - 1; i >= 0; i--)  
{  
  
}  
```  
  
 L’extrait **rfor** fournit une boucle for [basée sur une plage](http://msdn.microsoft.com/library/5750ba1d-ba48-4236-a923-e32de8345c2d) (lien) :  
  
```cpp  
for (auto& i : v)  
{  
  
}  
```  
  
## <a name="the-destructor-snippet-"></a>Extrait de code du destructeur (~)  
 L’extrait de code destructeur (**~**) présente un comportement différent dans des contextes différents. Si vous insérez cet extrait dans une classe, il fournit un destructeur pour cette classe. Examinons, par exemple, le code suivant :  
  
```cpp  
class SomeClass {  
  
};  
```  
  
 Si vous insérez l'extrait de code destructeur, il fournit un destructeur pour SomeClass :  
  
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
