---
title: Extraire l’interface, refactorisation (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdcf281e1ace40d1d7cdac0be302810ea173581b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667555"
---
# <a name="extract-interface-refactoring-c"></a>Refactorisation d'extraction d'interface (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’interface d’extraction est une opération de refactorisation qui fournit un moyen simple de créer une nouvelle interface avec des membres issus d’une classe, d’une structure ou d’une interface existante.

 Lorsque plusieurs clients utilisent le même sous-ensemble de membres d’une classe, d’une structure ou d’une interface, ou lorsque plusieurs classes, structures ou interfaces ont un sous-ensemble de membres en commun, il peut être utile d’utiliser le sous-ensemble de membres dans une interface. Pour plus d’informations sur l’utilisation des interfaces, consultez [interfaces](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).

 L’interface d’extraction génère une interface dans un nouveau fichier et positionne le curseur au début du nouveau fichier. Vous pouvez spécifier les membres à extraire dans la nouvelle interface, le nom de la nouvelle interface et le nom du fichier généré à l’aide de la boîte de dialogue **extraire l’interface** .

### <a name="to-use-extract-interface"></a>Pour utiliser l’interface Extract

1. Créez une application console nommée `ExtractInterface`, puis remplacez `Program` par le code suivant :

    ```csharp
    // Invoke Extract Interface on ProtoA.
    // Note:  the extracted interface will be created in a new file.
    class ProtoA
    {
        public void MethodB(string s) { }
    }
    ```

2. Avec le curseur positionné dans `MethodB`, puis cliquez sur **extraire l’interface** dans le menu **Refactoriser** .

     La boîte de dialogue **extraire l’interface** s’affiche.

     Vous pouvez également taper le raccourci clavier CTRL + R, I pour afficher la boîte de dialogue **extraire l’interface** .

     Vous pouvez également cliquer avec le bouton droit sur la souris, pointer sur **Refactoriser**, puis cliquer sur **extraire l’interface** pour afficher la boîte de dialogue **extraire l’interface** .

3. Cliquez sur **Sélectionner tout**.

4. Cliquez sur **OK**.

     Le nouveau fichier, IProtoA.cs et le code suivant s’affichent :

    ```csharp
    using System;
    namespace TopThreeRefactorings
    {
        interface IProtoA
        {
            void MethodB(string s);
        }
    }
    ```

## <a name="remarks"></a>Notes
 Cette fonctionnalité est accessible uniquement lorsque le curseur est positionné dans la classe, la structure ou l’interface qui contient les membres que vous souhaitez extraire. Lorsque le curseur se trouve à cette position, appelez l’opération d’extraction de l’interface d’extraction.

 Quand vous appelez l’interface d’extraction sur une classe ou sur un struct, la liste des bases et des interfaces est modifiée pour inclure le nouveau nom de l’interface. Lorsque vous appelez l’interface d’extraction sur une interface, la liste bases et interfaces n’est pas modifiée.

## <a name="see-also"></a>Voir aussi
 [Refactorisation (C#)](../csharp-ide/refactoring-csharp.md)