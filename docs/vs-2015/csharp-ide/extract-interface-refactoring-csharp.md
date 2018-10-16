---
title: Extraire l’Interface (refactorisation c#) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e7c3af675155cf3d47d82457aadbfb6327895d4f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279901"
---
# <a name="extract-interface-refactoring-c"></a>Refactorisation d'extraction d'interface (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extraire l’Interface est une opération de refactorisation qui offre un moyen facile de créer une nouvelle interface avec des membres qui proviennent d’une classe existante, un struct ou une interface.  
  
 Lorsque plusieurs clients utilisent le même sous-ensemble de membres à partir d’une classe, un struct ou une interface, ou lorsque plusieurs classes, structs ou interfaces ont en commun un sous-ensemble de membres, il peut être utile de mettre le sous-ensemble de membres dans une interface. Pour plus d’informations sur l’utilisation d’interfaces, consultez [Interfaces](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).  
  
 Extraire l’Interface génère une interface dans un nouveau fichier et place le curseur au début du nouveau fichier. Vous pouvez spécifier les membres à extraire dans la nouvelle interface, le nom de la nouvelle interface et le nom du fichier généré en utilisant le **extraire l’Interface** boîte de dialogue.  
  
### <a name="to-use-extract-interface"></a>Pour utiliser extraire l’Interface  
  
1.  Créez une application console nommée `ExtractInterface`, puis remplacez `Program` par le code suivant  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  Avec le curseur positionné dans `MethodB`, puis cliquez sur **extraire l’Interface** sur le **refactoriser** menu.  
  
     Le **extraire l’Interface** boîte de dialogue s’affiche.  
  
     Vous pouvez également taper le raccourci clavier CTRL + R, I pour afficher la **extraire l’Interface** boîte de dialogue.  
  
     Vous pouvez également cliquer sur la souris, pointez sur **refactoriser**, puis cliquez sur **extraire l’Interface** pour afficher le **extraire l’Interface** boîte de dialogue.  
  
3.  Cliquez sur **sélectionner tout**.  
  
4.  Cliquez sur **OK**.  
  
     Vous voyez le nouveau fichier, IProtoA.cs et le code suivant :  
  
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
 Cette fonctionnalité est uniquement accessible lorsque le curseur est positionné dans la classe, un struct ou une interface qui contient les membres que vous souhaitez extraire. Lorsque le curseur est dans cette position, appelez l’opération de refactorisation extraire l’Interface.  
  
 Lorsque vous appelez Extraire l’interface sur une classe ou un struct, la liste des bases et interfaces est modifiée pour inclure le nouveau nom de l’interface. Lorsque vous appelez Extraire l’interface sur une interface, la liste des bases et interfaces n’est pas modifiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Refactorisation (C#)](../csharp-ide/refactoring-csharp.md)