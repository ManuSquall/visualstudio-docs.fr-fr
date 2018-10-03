---
title: Encapsuler le champ (refactorisation c#) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 882ee68a1a5127cd46ff8ce5b6ea3350c95c6e8a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502657"
---
# <a name="encapsulate-field-refactoring-c"></a>Encapsuler le champ (Refactorisation C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le **encapsuler le champ** opération de refactorisation vous permet de créer rapidement une propriété à partir d’un champ existant et mettre en toute transparence à jour votre code avec des références à la nouvelle propriété.  
  
 Quand un [champ](http://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) est [public](http://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), autres objets ont un accès direct à ce champ et pouvez le modifier, sans être détectés par l’objet qui possède ce champ. À l’aide de [propriétés](http://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) pour encapsuler ce champ, vous pouvez interdire l’accès direct aux champs.  
  
 Pour créer la nouvelle propriété, le **encapsuler le champ** opération change le modificateur d’accès pour le champ que vous souhaitez encapsuler en [privé](http://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8), puis génère [obtenir](http://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71)et [définir](http://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) accesseurs pour ce champ. Dans certains cas, seul un accesseur `get` est généré, comme quand le champ est déclaré en lecture seule.  
  
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
  
     Vous pouvez également cliquer sur le curseur, pointer vers **refactoriser**, puis cliquez sur **encapsuler le champ** pour afficher le **encapsuler le champ** boîte de dialogue.  
  
4.  Spécifiez les paramètres.  
  
5.  Appuyez sur entrée ou cliquez sur le **OK** bouton.  
  
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
  
## <a name="remarks"></a>Notes  
 Le **encapsuler le champ** opération n’est possible que lorsque le curseur est positionné sur la même ligne que la déclaration de champ.  
  
 Pour les déclarations qui déclarent plusieurs champs, **encapsuler le champ** utilise la virgule comme limite entre les champs et initialise la refactorisation sur le champ qui est plus proche du curseur et sur la même ligne que le curseur. Vous pouvez également spécifier quel champ vous voulez encapsuler en sélectionnant le nom de ce champ dans la déclaration.  
  
 Le code généré par cette opération de refactorisation est modélisé par la fonctionnalité d'extraits de code Encapsuler le champ. Les extraits de code sont modifiables. Pour plus d’informations, consultez [Extraits de code](../ide/code-snippets.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Refactorisation (C#)](../csharp-ide/refactoring-csharp.md)   
 [Extraits de code Visual C#](../ide/visual-csharp-code-snippets.md)