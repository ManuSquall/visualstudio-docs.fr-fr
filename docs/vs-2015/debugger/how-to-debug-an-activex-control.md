---
title: 'Comment : déboguer un contrôle ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2cb1431b2be4c125b50ec45054e0d10685a2fe4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281734"
---
# <a name="how-to-debug-an-activex-control"></a>Comment : déboguer un contrôle ActiveX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Pour déboguer votre contrôle ActiveX, vous devez spécifier un conteneur (exécutable) à utiliser pour l'exécution du contrôle.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Pour spécifier un conteneur pour une session de débogage  
  
1.  Dans l'Explorateur de solutions, sélectionnez le projet.  
  
2.  À partir de la **vue** menu, choisissez **Pages de propriétés**.  
  
3.  Dans le **Pages de propriétés de projet** boîte de dialogue, ouvrez le **propriétés de Configuration** dossier, puis sélectionnez **débogage**.  
  
4.  Sous le **débogage** catégorie, recherchez le **commande** propriété.  
  
5.  Spécifiez le nom de chemin pour le conteneur. Par exemple, C:\Program Files\Internet Explorer\IEXPLORE.EXE.  
  
6.  Si vous spécifiez Internet Explorer comme conteneur et que vous utilisez Active Desktop, tapez `/new` dans le **Arguments de commande** boîte.  
  
7.  Cliquez sur **OK**.  
  
     Si vous ne spécifiez pas un conteneur dans le **Pages de propriétés de projet** boîte de dialogue, vous pouvez spécifier le conteneur lorsque vous commencerez le débogage. Lorsque vous sélectionnez une commande d’exécution pour démarrer le débogage, le [exécutable pour la boîte de dialogue de Session de débogage](../debugger/executable-for-debugging-session-dialog-box.md) s’affiche. Spécifiez le nom de chemin du conteneur dans la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Test des propriétés et des événements avec le conteneur de Test](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)   
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)



