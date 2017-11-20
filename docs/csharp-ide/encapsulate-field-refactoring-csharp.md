---
redirect_url: /visualstudio/csharp-ide/refactoring/encapsulate-field
title: Encapsuler le champ (refactorisation c#) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bd9e255b35ffb843c15d5ffa9c1547891bf437d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="encapsulate-field-refactoring-c"></a>Encapsuler le champ (Refactorisation C#)
Le **encapsuler le champ** l’opération de refactorisation vous permet de créer rapidement une propriété d’un champ existant et de mettre facilement à jour votre code avec des références à la nouvelle propriété.  
  
 Lorsqu’un [champ](/dotnet/csharp/programming-guide/classes-and-structs/fields) est [public](/dotnet/csharp/language-reference/keywords/public), autres objets ont un accès direct à ce champ et pouvez le modifier, sans être détectés par l’objet qui possède ce champ. À l’aide de [propriétés](/dotnet/csharp/programming-guide/classes-and-structs/properties) pour encapsuler ce champ, vous pouvez ne pas autoriser un accès direct aux champs.  
  
 Pour créer la nouvelle propriété, le **encapsuler le champ** opération modifie le modificateur d’accès pour le champ que vous voulez encapsuler à [privé](/dotnet/csharp/language-reference/keywords/private), puis génère [obtenir](/dotnet/csharp/language-reference/keywords/get)et [définir](/dotnet/csharp/language-reference/keywords/set) accesseurs pour ce champ. Dans certains cas, seul un accesseur `get` est généré, comme quand le champ est déclaré en lecture seule.  
  
 Le moteur de refactorisation met à jour votre code avec des références à la nouvelle propriété dans les zones spécifiées dans le **mise à jour les références** section de la **encapsuler le champ** boîte de dialogue.  
  
### <a name="to-create-a-property-from-a-field"></a>Pour créer une propriété à partir d'un champ  
  
1.  Créez une application console nommée `EncapsulateFieldExample`, puis remplacez `Program` par l'exemple de code suivant.  
  
    ```csharp  
    class Square  
    {  
        // Select the word 'width' and then use Encapsulate Field.  
        public int width, height;  
    }  
    class MainClass  
    {  
        public static void Main()  
        {  
            Square mySquare = new Square();  
            mySquare.width = 110;  
            mySquare.height = 150;  
            // Output values for width and height.  
            Console.WriteLine("width = {0}", mySquare.width);  
            Console.WriteLine("height = {0}", mySquare.height);  
        }  
    }  
    ```  
  
2.  Dans le [éditeur de Code](../ide/writing-code-in-the-code-and-text-editor.md), placez le curseur dans la déclaration, sur le nom du champ que vous voulez encapsuler. Dans l'exemple ci-dessous, placez le curseur sur le mot `width` :  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  Sur le **refactoriser** menu, cliquez sur **encapsuler le champ**.  
  
     Le **encapsuler le champ** boîte de dialogue s’affiche.  
  
     Vous pouvez également taper le raccourci clavier CTRL + R, E pour afficher la **encapsuler le champ** boîte de dialogue.  
  
     Vous pouvez cliquer également sur le curseur, pointez sur **refactoriser**, puis cliquez sur **encapsuler le champ** pour afficher les **encapsuler le champ** boîte de dialogue.  
  
4.  Spécifiez les paramètres.  
  
5.  Appuyez sur entrée, ou cliquez sur le **OK** bouton.  
  
6.  Si vous avez sélectionné le **aperçu des modifications de référence** option, puis le **aperçu des modifications de référence** fenêtre s’ouvre. Cliquez sur le **appliquer** bouton.  
  
     Le code d'accesseur `get` et `set` suivant est affiché dans votre fichier source :  
  
    ```csharp  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     Le code dans la méthode `Main` est également mis à jour en fonction du nouveau nom de propriété `Width`.  
  
    ```csharp  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## <a name="remarks"></a>Remarques  
 Le **encapsuler le champ** opération est uniquement possible lorsque le curseur est positionné sur la même ligne que la déclaration de champ.  
  
 Pour les déclarations qui déclarent plusieurs champs, **encapsuler le champ** utilise la virgule comme limite entre les champs et initialise la refactorisation sur le champ qui est le plus proche du curseur et sur la même ligne que le curseur. Vous pouvez également spécifier quel champ vous voulez encapsuler en sélectionnant le nom de ce champ dans la déclaration.  
  
 Le code généré par cette opération de refactorisation est modélisé par la fonctionnalité d'extraits de code Encapsuler le champ. Les extraits de code sont modifiables. Pour plus d’informations, consultez [Extraits de code](../ide/visual-csharp-code-snippets.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Refactorisation (C#)](refactoring-csharp.md)   
 [Extraits de code Visual C#](../ide/visual-csharp-code-snippets.md)