---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-interface
title: "Extraire l’Interface (refactorisation c#) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: e3e606a86f5989ca928e0b093b564f997f92a559
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="extract-interface-refactoring-c"></a>Refactorisation d'extraction d'interface (C#)
Extraire l’Interface est une opération de refactorisation qui offre un moyen simple pour créer une nouvelle interface avec des membres qui proviennent d’une classe existante, un struct ou une interface.  
  
 Lorsque plusieurs clients utilisent le même sous-ensemble de membres à partir d’une classe, un struct ou une interface, ou lorsque plusieurs classes, structs ou interfaces ont en commun un sous-ensemble de membres, il peut être utile de sont basées sur le sous-ensemble de membres dans une interface. Pour plus d’informations sur l’utilisation d’interfaces, consultez [Interfaces](/dotnet/csharp/programming-guide/interfaces/index).  
  
 Extraire l’Interface génère une interface dans un nouveau fichier et place le curseur au début du nouveau fichier. Vous pouvez spécifier les membres à extraire dans la nouvelle interface, le nom de la nouvelle interface et le nom du fichier généré en utilisant la **extraire l’Interface** boîte de dialogue.  
  
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
  
2.  Avec le curseur positionné dans `MethodB`, puis cliquez sur **extraire l’Interface** sur la **refactoriser** menu.  
  
     Le **extraire l’Interface** boîte de dialogue s’affiche.  
  
     Vous pouvez également taper le raccourci clavier CTRL + R, I pour afficher la **extraire l’Interface** boîte de dialogue.  
  
     Vous pouvez cliquer également sur la souris, pointez sur **refactoriser**, puis cliquez sur **extraire l’Interface** pour afficher les **extraire l’Interface** boîte de dialogue.  
  
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
 Cette fonctionnalité est accessible uniquement lorsque le curseur est positionné dans la classe, struct ou interface qui contient les membres que vous souhaitez extraire. Lorsque le curseur est dans cette position, appelez l’opération de refactorisation extraire l’Interface.  
  
 Lorsque vous appelez Extraire l’interface sur une classe ou un struct, la liste des bases et des interfaces est modifiée pour inclure le nouveau nom de l’interface. Lorsque vous appelez Extraire l’interface sur une interface, la liste des bases et des interfaces n’est pas modifiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Refactorisation (C#)](refactoring-csharp.md)