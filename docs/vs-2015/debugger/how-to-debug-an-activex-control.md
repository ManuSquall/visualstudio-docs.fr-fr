---
title: 'Comment : déboguer un contrôle ActiveX | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9524ab08ab955609f29f437e8a1576af02738aa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704463"
---
# <a name="how-to-debug-an-activex-control"></a>Comment : déboguer un contrôle ActiveX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Pour déboguer votre contrôle ActiveX, vous devez spécifier un conteneur (exécutable) à utiliser pour l'exécution du contrôle.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Pour spécifier un conteneur pour une session de débogage  
  
1. Dans l’Explorateur de solutions, sélectionnez le projet.  
  
2. Dans le menu **affichage** , cliquez sur **pages de propriétés**.  
  
3. Dans la boîte de dialogue **Pages de propriété de projet**, ouvrez le dossier **Propriétés de configuration** et sélectionnez **Débogage**.  
  
4. Dans la catégorie **Débogage**, recherchez la propriété **Commande**.  
  
5. Spécifiez le nom de chemin pour le conteneur. Par exemple, C:\Program Files\Internet Explorer\IEXPLORE.EXE.  
  
6. Si vous spécifiez Internet Explorer comme conteneur et que vous utilisez Active Desktop, tapez `/new` dans la zone **Arguments de la commande**.  
  
7. Cliquez sur **OK**.  
  
     Si vous ne spécifiez pas un conteneur dans la boîte de dialogue **Pages de propriétés de projet**, vous pouvez spécifier le conteneur quand vous commencez à déboguer. Quand vous sélectionnez une commande d’exécution pour commencer le débogage, la [boîte de dialogue Exécutable pour la session de débogage](../debugger/executable-for-debugging-session-dialog-box.md) s’affiche. Spécifiez le nom de chemin du conteneur dans la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Test des propriétés et des événements avec le conteneur de test](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)   
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)
