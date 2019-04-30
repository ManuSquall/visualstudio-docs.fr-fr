---
title: Renommer (refactorisation c#) | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 971ca4e94f28016335483a03f4b0121de587f00d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439957"
---
# <a name="rename-refactoring-c"></a>Refactorisation de changement de nom (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Renommer** est une fonctionnalité de refactorisation dans l’environnement de développement intégré (IDE) Visual Studio qui offre un moyen facile de renommer les identificateurs pour les symboles de code tels que les champs, les variables locales, les méthodes, les espaces de noms, les propriétés et les types. **Renommer** peut être utilisé pour modifier les noms dans les commentaires et les chaînes et pour modifier les déclarations et les appels d’un identificateur.  
  
> [!NOTE]
> Lorsque vous utilisez le contrôle de code Source pour Visual Studio, obtenez la dernière version de sources avant d’essayer d’effectuer la refactorisation de changement de nom.  
  
 Refactorisation de changement de nom est disponible dans les fonctionnalités de Visual Studio suivantes :  
  
|Fonctionnalité|Comportement de la refactorisation dans l’IDE|  
|-------------|----------------------------------------|  
|Éditeur de code|Dans l’éditeur de Code, la refactorisation de changement de nom est disponible lorsque vous positionnez le curseur sur certains types de symboles de code. Lorsque le curseur se trouve dans cette position, vous pouvez appeler la **renommer** commande en tapant le raccourci clavier (CTRL + R, CTRL + R), ou en sélectionnant le **renommer** commande à partir d’une balise active, menu contextuel ou le  **Refactoriser** menu.|  
|Affichage de classes|Lorsque vous sélectionnez un identificateur dans l’affichage de classes, la refactorisation de changement de nom est disponible dans le menu contextuel et **refactoriser** menu.|  
|Explorateur d'objets|Lorsque vous sélectionnez un identificateur dans l’Explorateur d’objets, la refactorisation de changement de nom est uniquement disponible à partir de la **refactoriser** menu.|  
|Grille des propriétés du Concepteur Windows Forms|Dans le **grille des propriétés** du Concepteur Windows Forms, la modification du nom d’un contrôle déclenchera une opération de changement de nom pour ce contrôle. Le **renommer** boîte de dialogue s’affiche pas.|  
|Explorateur de solutions|Dans **l’Explorateur de solutions**, un **renommer** commande est disponible dans le menu contextuel. Si le fichier source sélectionné contient une classe dont nom de classe est le même que le nom de fichier, vous pouvez utiliser cette commande pour renommer le fichier source et exécuter la refactorisation de changement de nom simultanément.<br /><br /> Par exemple, si vous créez une application Windows par défaut, puis renommez Form1.cs en TestForm.cs, le nom de fichier source Form1.cs devient TestForm.cs et la classe Form1 et toutes les références à cette classe est renommée TestForm. **Remarque :**  Le **Annuler** commande (CTRL + Z) annuler la refactorisation de changement de nom dans le code et uniquement sera pas les changez le nom du fichier de sauvegarde pour le nom d’origine. <br /><br /> Si le fichier source sélectionné ne contient pas une classe dont le nom est le même que le nom de fichier, le **renommer** commande **l’Explorateur de solutions** renommera uniquement le fichier source et n’exécutera pas de changement de nom la refactorisation.|  
  
## <a name="rename-operations"></a>Renommer des opérations  
 Lorsque vous exécutez **renommer**, le moteur de refactorisation exécute une opération de changement de nom spécifique pour chaque symbole de code, comme décrit dans le tableau suivant.  
  
|Symbole de code|Changement de nom|  
|-----------------|----------------------|  
|Champ|Modifie la déclaration et les utilisations du champ vers le nouveau nom.|  
|variable locale|Modifie la déclaration et les utilisations de la variable vers le nouveau nom.|  
|Méthode|Modifie le nom de la méthode et toutes les références à cette méthode pour le nouveau nom. **Remarque :**  Lorsque vous renommez une méthode d’extension, l’opération de changement de nom se propage à toutes les instances de la méthode qui sont dans la portée, même si la méthode d’extension est utilisée comme une méthode statique ou une méthode d’instance. Pour plus d’informations, consultez [Méthodes d’extension](http://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|  
|Espace de noms|Modifie le nom de l’espace de noms pour le nouveau nom dans la déclaration, toutes les `using` instructions et des noms qualifiés complets. **Remarque :**  Lorsque vous renommez un espace de noms, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] met également à jour le **Namespace par défaut** propriété sur le **Application** page de la **Concepteur de projet**. Cette propriété ne peut pas être réinitialisée en sélectionnant **Annuler** à partir de la **modifier** menu. Pour réinitialiser le **Namespace par défaut** valeur de propriété, vous devez modifier la propriété dans le **Concepteur de projet**. Pour plus d’informations, consultez [Page Application](../ide/reference/application-page-project-designer-csharp.md).|  
|Propriété|Modifie la déclaration et les utilisations de la propriété vers le nouveau nom.|  
|Type|Modifie toutes les déclarations et toutes les utilisations du type vers le nouveau nom, y compris les constructeurs et destructeurs. Pour les types partiels, l’opération de changement de nom se propage à toutes les parties.|  
  
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
  
2. Placez le curseur sur `MethodB`, soit dans la déclaration de méthode ou de l’appel de méthode.  
  
3. À partir de la **refactoriser** menu, sélectionnez **renommer**. Le **renommer** boîte de dialogue s’affiche.  
  
     Vous pouvez également cliquer sur le curseur, pointer vers **refactoriser** dans le menu contextuel, puis cliquez sur **renommer** pour afficher le **renommer** boîte de dialogue.  
  
4. Dans le **nouveau nom** , tapez `MethodC`.  
  
5. Sélectionnez le **rechercher dans les commentaires** case à cocher.  
  
6. Cliquez sur **OK**.  
  
7. Dans le **aperçu des modifications** boîte de dialogue, cliquez sur **appliquer**.  
  
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
  
2. Dans la déclaration pour `MethodB`, tapez ou revenir en arrière sur l’identificateur de méthode. Une invite de balise active apparaît sous cet identificateur.  
  
    > [!NOTE]
    > Vous pouvez uniquement appeler la refactorisation de changement de nom à l’aide de balises actives à la déclaration d’un identificateur.  
  
3. Tapez le raccourci clavier MAJ + ALT + F10, puis appuyez sur la flèche vers le bas pour afficher le menu balise active.  
  
     - ou -  
  
     Déplacez le pointeur de la souris sur l’invite de balise active pour afficher la balise active. Déplacez le pointeur de la souris sur la balise active, puis cliquez sur la flèche vers le bas pour afficher le menu balise active.  
  
4. Sélectionnez le **renommer '\<identifer1 >' à '\<identificateur2 >'** élément de menu pour appeler la refactorisation de changement de nom sans aperçu des modifications à votre code. Toutes les références à  **\<identifer1 >** seront automatiquement mis à jour vers  **\<identificateur2 >**.  
  
     - ou -  
  
     Sélectionnez le **renommer avec l’aperçu** élément de menu pour appeler la refactorisation de changement de nom avec un aperçu des modifications à votre code. Le **aperçu des modifications** boîte de dialogue s’affiche.  
  
## <a name="remarks"></a>Notes  
  
## <a name="renaming-implemented-or-overridden-members"></a>Modification du nom des membres implémentés ou substitués  
 Lorsque vous **renommer** un membre qui implémente/substitue ou est implémenté/remplacées par les membres dans d’autres types, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] affiche une boîte de dialogue indiquant que l’opération de changement entraînera des mises à jour en cascade. Si vous cliquez sur **continuer**, la refactorisation de manière récursive moteur recherche et renomme tous les membres de base et des types dérivés qui ont implémente/remplacements relations avec le membre qui est renommé.  
  
 L’exemple de code suivant contient les membres avec des relations implémente/substitue.  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]  
  
 Dans l’exemple précédent, changement de nom `C.Method()` renomme également `Ibase.Method()` car `C.Method()` implémente `Ibase.Method()`. Ensuite, la refactorisation de manière récursive moteur voit que `Ibase.Method()` est implémentée par `Derived.Method()` et renomme `Derived.Method()`. Le moteur de refactorisation ne renomme pas `Base.Method()`, car `Derived.Method()` ne se substitue pas `Base.Method()`. Le moteur de refactorisation est arrêté, sauf si vous avez **renommer les surcharges** archivé le **renommer** boîte de dialogue.  
  
 Si **renommer les surcharges** est activée, le moteur de refactorisation renomme `Derived.Method(int i)` , car il surcharge `Derived.Method()`, `Base.Method(int i)` , car il est remplacé par `Derived.Method(int i)`, et `Base.Method()` , car il existe une surcharge de `Base.Method(int i)`.  
  
> [!NOTE]
> Lorsque vous renommez un membre qui a été défini dans un assembly référencé, une boîte de dialogue explique que le changement de nom provoquera des erreurs de build.  
  
## <a name="renaming-properties-of-anonymous-types"></a>Renommage des propriétés de Types anonymes  
 Lorsque vous renommez une propriété dans les types anonymes, l’opération de changement de nom se propagera aux propriétés dans d’autres types anonymes qui ont les mêmes propriétés. Les exemples suivants illustrent ce comportement.  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 Dans le code précédent, changement de nom `ID` changera `ID` dans les deux instructions parce qu’ils ont le même type anonyme sous-jacent.  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 Dans le code précédent, changement de nom `ID` renommera uniquement une instance de `ID` car `companyIDs` et `orderIDs` n’ont pas les mêmes propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Refactorisation (C#)](../csharp-ide/refactoring-csharp.md)   
 [Types anonymes](http://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)