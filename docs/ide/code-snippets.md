---
title: Extraits de code
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: c06f9f7dc7e5a672e3fd5da3f3fc834fe223a783
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585416"
---
# <a name="code-snippets"></a>Extraits de code

Les extraits de code sont de petits blocs de code réutilisables que l’on peut insérer dans un fichier de code à l’aide d’une commande de menu contextuel (clic droit) ou d’une combinaison de touches d’accès rapide. Ils contiennent généralement des blocs de code fréquemment utilisés, tels que les blocs `try-finally` ou `if-else`, mais ils permettent d’insérer des classes ou des méthodes entières.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Extraits de code (Visual Studio pour Mac)](/visualstudio/mac/snippets).

Les extraits de code sont disponibles dans de nombreux langages : C#, C++, Visual Basic, XML, T-SQL, etc. Pour afficher tous les extraits de code installés disponibles pour une langue, ouvrez le **Gestionnaire des extraits de code** à partir du menu **Outils** (ou appuyez sur **CTRL** + **K**, **CTRL** + **B**), puis choisissez la langue dans le menu déroulant en haut.

![Boîte de dialogue Gestionnaire des extraits de code](media/code-snippets-manager.png)

Pour accéder aux extraits de code, plusieurs méthodes générales s’offrent à vous :

- Dans la barre de menus, choisissez **modifier**l’extrait de code d'  >  **IntelliSense**  >  **insertion** IntelliSense

- Dans le menu contextuel, cliquez avec le bouton droit dans l’éditeur de code, choisissez **extrait**  >  **Insérer un extrait**

- À partir du clavier, appuyez sur **CTRL** + **K**,**CTRL** + **X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Extraits d’expansion et extraits Entourer de

Dans Visual Studio, il existe deux types d'extrait de code : les extraits d'extension, qui sont ajoutés à un point d'insertion spécifié et qui peuvent remplacer un raccourci d'extrait de code, et les extraits de code d'encerclement (C# et C++ uniquement), qui sont ajoutés autour d'un bloc de code sélectionné.

Exemple d'extrait de code d'extension : en C#, le raccourci tryf est utilisé pour insérer un bloc try-finally :

```csharp
try
{

}
finally
{

}
```

Vous pouvez insérer cet extrait de code en cliquant sur **Insérer un extrait** dans le menu contextuel (menu contextuel) de la fenêtre de code, puis sur **Visual C#**, tapez `tryf` et appuyez sur la touche **Tab**. Ou, vous pouvez taper `tryf` et appuyer deux fois sur la **touche Tab** .

Exemple d'extrait de code d'encerclement : en C++, le raccourci `if` peut être utilisé comme un extrait d'insertion ou comme un extrait de code d'encerclement. Si vous sélectionnez une ligne de code (par exemple `return FALSE;` ), puis choisissez **entourer**de  >  **si**, l’extrait de code est développé autour de la ligne :

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Paramètres de remplacement d’extrait de code

Les extraits de code peuvent contenir des paramètres de remplacement, qui sont des espaces réservés que vous devez remplacer en fonction du code précis que vous écrivez. Dans l'exemple précédent, `true` est un paramètre de remplacement, que vous pouvez remplacer par la condition appropriée. Cette condition que vous apportez est répétée pour chaque instance du même paramètre de remplacement dans l'extrait de code.

Par exemple, en Visual Basic, il existe un extrait de code qui insère une propriété. Pour insérer l’extrait de code, choisissez **Snippet**  >  **Insérer un extrait** dans le menu contextuel d’un Visual Basic fichier de code. Ensuite, choisissez **modèles de code**  >  **Propriétés, procédures, événements**  >  **définir une propriété**.

![Menu Extrait de code pour Définir une propriété](media/code-snippets-vb-property.png)

Le code suivant est inséré :

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

Si vous remplacez `newPropertyValue` par `m_property`, chaque instance de `newPropertyValue` est modifiée. Si vous remplacez `String` par `Int` dans la déclaration de propriété, la valeur de la méthode set est également remplacée par `Int`.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : création d’un extrait de code](../ide/walkthrough-creating-a-code-snippet.md)
- [Comment : distribuer des extraits de code](../ide/how-to-distribute-code-snippets.md)
- [Meilleures pratiques pour l’utilisation des extraits de code](../ide/best-practices-for-using-code-snippets.md)
- [Dépannage des extraits de code](../ide/troubleshooting-snippets.md)
- [Extraits de code C#](../ide/visual-csharp-code-snippets.md)
- [Extraits de code C++](../ide/visual-cpp-code-snippets.md)
- [Référence de schéma des extraits de code](../ide/code-snippets-schema-reference.md)
- [Extraits de code (Visual Studio pour Mac)](/visualstudio/mac/snippets)
