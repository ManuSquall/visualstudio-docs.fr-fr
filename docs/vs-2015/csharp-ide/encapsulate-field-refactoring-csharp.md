---
title: Encapsuler la refactorisationC#de champ () | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b4f5ddbe7eab925b06584f00b04bed3c74e9811
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667568"
---
# <a name="encapsulate-field-refactoring-c"></a>Encapsuler le champ (Refactorisation C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’opération de refactorisation **encapsuler le champ** vous permet de créer rapidement une propriété à partir d’un champ existant, puis de mettre à jour votre code en toute transparence avec des références à la nouvelle propriété.

 Lorsqu’un [champ](https://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) est [public](https://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), les autres objets ont un accès direct à ce champ et peuvent le modifier, ce qui n’est pas détecté par l’objet qui possède ce champ. En utilisant des [Propriétés](https://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) pour encapsuler ce champ, vous pouvez interdire l’accès direct aux champs.

 Pour créer la nouvelle propriété, l’opération **encapsuler le champ** modifie le modificateur d’accès pour le champ que vous souhaitez encapsuler en [privé](https://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8), puis génère des accesseurs d' [extraction](https://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71) et de [définition](https://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) pour ce champ. Dans certains cas, seul un accesseur `get` est généré, comme quand le champ est déclaré en lecture seule.

 Le moteur de refactorisation met à jour votre code avec des références à la nouvelle propriété dans les zones spécifiées dans la section **mettre à jour les références** de la boîte de dialogue **encapsuler le champ** .

### <a name="to-create-a-property-from-a-field"></a>Pour créer une propriété à partir d'un champ

1. Créez une application console nommée `EncapsulateFieldExample`, puis remplacez `Program` par l'exemple de code suivant.

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

2. Dans l' [éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md), placez le curseur dans la déclaration, sur le nom du champ que vous souhaitez encapsuler. Dans l'exemple ci-dessous, placez le curseur sur le mot `width` :

    ```csharp
    public int width, height;
    ```

3. Dans le menu **Refactoriser** , cliquez sur **encapsuler le champ**.

     La boîte de dialogue **encapsuler le champ** s’affiche.

     Vous pouvez également taper le raccourci clavier CTRL + R, E pour afficher la boîte de dialogue **encapsuler le champ** .

     Vous pouvez également cliquer avec le bouton droit sur le curseur, pointer sur **Refactoriser**, puis cliquer sur **encapsuler le champ** pour afficher la boîte de dialogue **encapsuler le champ** .

4. Spécifiez les paramètres.

5. Appuyez sur entrée ou cliquez sur le bouton **OK** .

6. Si vous avez sélectionné l’option **aperçu des modifications de référence** , la fenêtre Aperçu des modifications de la **référence** s’ouvre. Cliquez sur le bouton **appliquer** .

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
 L’opération d' **encapsulation de champ** est possible uniquement lorsque le curseur est positionné sur la même ligne que la déclaration de champ.

 Pour les déclarations qui déclarent plusieurs champs, **encapsuler le champ** utilise la virgule comme limite entre les champs et initialise la refactorisation sur le champ le plus proche du curseur et sur la même ligne que le curseur. Vous pouvez également spécifier quel champ vous voulez encapsuler en sélectionnant le nom de ce champ dans la déclaration.

 Le code généré par cette opération de refactorisation est modélisé par la fonctionnalité d'extraits de code Encapsuler le champ. Les extraits de code sont modifiables. Pour plus d'informations, consultez [Code Snippets](../ide/code-snippets.md).

## <a name="see-also"></a>Voir aussi
 [Extraits de code visuelC#](../csharp-ide/refactoring-csharp.md) [ C# ](../ide/visual-csharp-code-snippets.md) de refactorisation ()