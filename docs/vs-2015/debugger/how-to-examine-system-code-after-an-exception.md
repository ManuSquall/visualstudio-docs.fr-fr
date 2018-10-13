---
title: 'Comment : examiner du Code système après une Exception | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91b0f0ba806868420b56f59d1b3f6de99a87886b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255773"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Comment : examiner du code système après une exception
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsqu'une exception est levée, il peut s'avérer nécessaire d'examiner le code dans un appel système afin de déterminer la cause de l'exception. Pour ce faire, suivez la procédure ci-dessous si aucun symbole n'est chargé pour le code système ou si l'option Uniquement mon code est activée.  
  
### <a name="to-examine-system-code-following-an-exception"></a>Pour examiner du code système après une exception  
  
1.  Dans le **pile des appels** fenêtre, avec le bouton droit, puis cliquez sur **afficher le Code externe**.  
  
     Si l'option Uniquement mon code n'est pas activée, cette option n'est pas disponible dans le menu contextuel et le code système s'affiche par défaut.  
  
2.  Cliquez sur les frames de code externe qui s’affichent maintenant dans le **pile des appels** fenêtre.  
  
3.  Pointez sur **charger les symboles depuis** puis cliquez sur **serveurs de symboles Microsoft**.  
  
    1.  Si l'option Uniquement mon code était activée, une boîte de dialogue s'affiche pour indiquer que cette option est à présent désactivée, ce qui est nécessaire pour effectuer un pas à pas détaillé dans les appels système.  
  
    2.  Le **téléchargement des symboles publics** boîte de dialogue s’affiche. puis se ferme une fois le téléchargement terminé.  
  
4.  Vous pouvez maintenant examiner le code système dans le **pile des appels** fenêtre et les autres fenêtres. Par exemple, vous pouvez double-cliquer sur un frame de pile d’appel pour afficher le code dans une source ou **désassemblage** fenêtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)





