---
title: Refactorisation de changement deC#nom () | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0db7696268e5e3d24d005fbf35a08b330f2dc849
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667480"
---
# <a name="rename-refactoring-c"></a>Refactorisation de changement de nom (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Renommer** est une fonctionnalité de refactorisation de l’environnement de développement intégré (IDE) de Visual Studio qui permet de renommer facilement les identificateurs pour les symboles de code, tels que les champs, les variables locales, les méthodes, les espaces de noms, les propriétés et les types. **Renommer** peut être utilisé pour modifier les noms dans les commentaires et dans les chaînes, et pour modifier les déclarations et les appels d’un identificateur.

> [!NOTE]
> Lorsque vous utilisez le contrôle de code source pour Visual Studio, procurez-vous la dernière version des sources avant d’essayer d’effectuer une refactorisation de changement de nom.

 La refactorisation de changement de nom est disponible à partir des fonctionnalités Visual Studio suivantes :

|Fonction|Comportement de la refactorisation dans l’IDE|
|-------------|----------------------------------------|
|Éditeur de code|Dans l’éditeur de code, la refactorisation de changement de nom est disponible lorsque vous placez le curseur sur certains types de symboles de code. Lorsque le curseur se trouve à cette position, vous pouvez appeler la commande **Renommer** en tapant le raccourci clavier (Ctrl + r, Ctrl + r) ou en sélectionnant la commande **Renommer** dans une balise active, un menu contextuel ou le menu **Refactoriser** .|
|Affichage de classes|Lorsque vous sélectionnez un identificateur dans Affichage de classes, renommer la refactorisation est disponible dans le menu contextuel et dans le menu **Refactoriser** .|
|Explorateur d'objets|Lorsque vous sélectionnez un identificateur dans l’Explorateur d’objets, la refactorisation de changement de nom est disponible uniquement à partir du menu **Refactoriser** .|
|Grille des propriétés de la Concepteur Windows Forms|Dans la **grille des propriétés** de la Concepteur Windows Forms, la modification du nom d’un contrôle lance une opération de changement de nom pour ce contrôle. La boîte de dialogue **Renommer** ne s’affiche pas.|
|l'Explorateur de solutions|Dans **Explorateur de solutions**, une commande **Renommer** est disponible dans le menu contextuel. Si le fichier source sélectionné contient une classe dont le nom de classe est le même que le nom de fichier, vous pouvez utiliser cette commande pour renommer simultanément le fichier source et exécuter la refactorisation de changement de nom.<br /><br /> Par exemple, si vous créez une application Windows par défaut, puis renommez Form1.cs en TestForm.cs, le nom de fichier source Form1.cs passe à TestForm.cs et la classe Form1 et toutes les références à cette classe sont renommées en TestForm. **Remarque :**  La commande **Annuler** (Ctrl + Z) annule uniquement la refactorisation de changement de nom dans le code et ne rétablit pas le nom d’origine du fichier. <br /><br /> Si le fichier source sélectionné ne contient pas de classe dont le nom est identique au nom de fichier, la commande **Renommer** dans **Explorateur de solutions** renomme uniquement le fichier source et n’exécute pas la refactorisation de changement de nom.|

## <a name="rename-operations"></a>Opérations de changement de nom
 Quand vous exécutez **Rename**, le moteur de refactorisation exécute une opération de changement de nom spécifique pour chaque symbole de code, comme décrit dans le tableau suivant.

|Symbole de code|Opération de changement de nom|
|-----------------|----------------------|
|Champ|Remplace la déclaration et les utilisations du champ par le nouveau nom.|
|Variable locale|Remplace la déclaration et les utilisations de la variable par le nouveau nom.|
|Méthode|Remplace le nom de la méthode et toutes les références à cette méthode par le nouveau nom. **Remarque :**  Lorsque vous renommez une méthode d’extension, l’opération de changement de nom se propage à toutes les instances de la méthode qui sont dans la portée, que la méthode d’extension soit utilisée en tant que méthode statique ou méthode d’instance. Pour plus d’informations, consultez [Méthodes d’extension](https://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|
|Espace de noms|Remplace le nom de l’espace de noms par le nouveau nom dans la déclaration, toutes les instructions `using` et les noms qualifiés complets. **Remarque :**  Quand vous renommez un espace de noms, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] met également à jour la propriété **espace de noms par défaut** sur la page **application** du **Concepteur de projet**. Cette propriété ne peut pas être réinitialisée en sélectionnant **Annuler** dans le menu **Edition** . Pour réinitialiser la valeur de la propriété **espace de noms par défaut** , vous devez modifier la propriété dans le **Concepteur de projet**. Pour plus d’informations, consultez la [page application](../ide/reference/application-page-project-designer-csharp.md).|
|Property|Remplace la déclaration et les utilisations de la propriété par le nouveau nom.|
|Tapez|Remplace toutes les déclarations et toutes les utilisations du type par le nouveau nom, y compris les constructeurs et les destructeurs. Pour les types partiels, l’opération de changement de nom se propage à toutes les parties.|

#### <a name="to-rename-an-identifier"></a>Pour renommer un identificateur

1. Créez une application console nommée `RenameIdentifier`, puis remplacez `Program` par l'exemple de code suivant.

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. Placez le curseur sur `MethodB`, dans la déclaration de la méthode ou l’appel de la méthode.

3. Dans le menu **Refactoriser** , sélectionnez **Renommer**. La boîte de dialogue **Renommer** s’affiche.

     Vous pouvez également cliquer avec le bouton droit sur le curseur, pointer sur **Refactoriser** dans le menu contextuel, puis cliquer sur **Renommer** pour afficher la boîte de dialogue **Renommer** .

4. Dans le champ **nouveau nom** , tapez `MethodC`.

5. Activez la case à cocher **Rechercher dans les commentaires** .

6. Cliquez sur **OK**.

7. Dans la boîte de dialogue **aperçu des modifications** , cliquez sur **appliquer**.

#### <a name="to-rename-an-identifier-using-smart-tags"></a>Pour renommer un identificateur à l’aide de balises actives

1. Créez une application console nommée `RenameIdentifier`, puis remplacez `Program` par l'exemple de code suivant.

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. Dans la déclaration pour `MethodB`, tapez ou retour arrière sur l’identificateur de méthode. Une invite de balise active apparaît sous cet identificateur.

    > [!NOTE]
    > Vous pouvez appeler la refactorisation de changement de nom uniquement à l’aide de balises actives au niveau de la déclaration d’un identificateur.

3. Tapez le raccourci clavier MAJ + ALT + F10, puis appuyez sur la flèche bas pour afficher le menu de la balise active.

     ou

     Déplacez le pointeur de la souris sur l’invite de la balise active pour afficher la balise active. Placez le pointeur de la souris sur la balise active, puis cliquez sur la flèche vers le bas pour afficher le menu de la balise active.

4. Sélectionnez l’élément de menu **Renommer « \<identifer1 > » en « \<identifier2 > »** pour appeler la refactorisation de changement de nom sans aperçu des modifications apportées à votre code. Toutes les références à **\<identifer1 >** seront automatiquement mises à jour pour **\<identifier2 >** .

     ou

     Sélectionnez l’élément de menu **Renommer avec l’aperçu** pour appeler refactorisation de renommage avec un aperçu des modifications apportées à votre code. La boîte de dialogue **aperçu des modifications** s’affiche.

## <a name="remarks"></a>Notes

## <a name="renaming-implemented-or-overridden-members"></a>Attribution d’un nouveau nom aux membres implémentés ou substitués
 Lorsque vous **renommez** un membre qui implémente/substitue ou est implémenté/substitué par des membres dans d’autres types, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] affiche une boîte de dialogue qui indique que l’opération de changement de nom entraîne des mises à jour en cascade. Si vous cliquez sur **Continuer**, le moteur de refactorisation recherche et renomme de manière récursive tous les membres des types de base et dérivés qui ont implémente/substitue des relations avec le membre renommé.

 L’exemple de code suivant contient des membres avec des relations Implements/Overrides.

 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]

 Dans l’exemple précédent, le fait de renommer `C.Method()` renomme également `Ibase.Method()`, car `C.Method()` implémente `Ibase.Method()`. Ensuite, le moteur de refactorisation détecte de manière récursive que `Ibase.Method()` est implémenté par `Derived.Method()` et renomme `Derived.Method()`. Le moteur de refactorisation ne renomme pas `Base.Method()`, car `Derived.Method()` ne remplace pas `Base.Method()`. Le moteur de refactorisation s’arrête ici, sauf si vous avez coché l’option **Renommer les surcharges** dans la boîte de dialogue **Renommer** .

 Si la case à cocher **Renommer les surcharges** est activée, le moteur de refactorisation renomme `Derived.Method(int i)`, car il surcharge `Derived.Method()`, `Base.Method(int i)` parce qu’il est substitué par `Derived.Method(int i)`, et `Base.Method()` parce qu’il s’agit d’une surcharge de `Base.Method(int i)`.

> [!NOTE]
> Lorsque vous renommez un membre qui a été défini dans un assembly référencé, une boîte de dialogue explique que le changement de nom entraîne des erreurs de Build.

## <a name="renaming-properties-of-anonymous-types"></a>Attribution d’un nouveau nom aux propriétés des types anonymes
 Lorsque vous renommez une propriété dans des types anonymes, l’opération de changement de nom se propage aux propriétés d’autres types anonymes qui ont les mêmes propriétés. Les exemples suivants illustrent ce comportement.

```csharp
var a = new { ID = 1};
var b = new { ID = 2};
```

 Dans le code précédent, le fait de renommer `ID` change `ID` dans les deux instructions, car elles ont le même type anonyme sous-jacent.

```csharp
var companyIDs =
    from c in companylist
    select new { ID = c.ID, Name = c.Name};

var orderIDs =
    from o in orderlist
    select new { ID = o.ID, Item = o.Name};
```

 Dans le code précédent, le fait de renommer `ID` renomme une seule instance de `ID`, car `companyIDs` et `orderIDs` n’ont pas les mêmes propriétés.

## <a name="see-also"></a>Voir aussi
 [Types anonymes](https://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b) [deC#refactorisation ()](../csharp-ide/refactoring-csharp.md)