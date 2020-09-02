---
title: Boîte de dialogue Modifier & Continuer-message d’erreur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5437ef982309ef8595f08283f2685e93d346e764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428277"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Message d'erreur de Modifier &amp; Continuer, boîte de dialogue
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette boîte de dialogue apparaît lorsque vous déboguez dans un langage qui prend en charge modifier & continuer, mais que **modifier & continuer** n’est pas disponible pour le type de modifications de code que vous avez apportées. Le message d'erreur affiché dans la boîte de dialogue fournit une explication plus détaillée. Les raisons pouvant justifier l'affichage de cette boîte de dialogue sont les suivantes :  
  
- Vous avez essayé de modifier un code managé alors que le débogage non managé était activé. Modifier &amp; Continuer ne fonctionne pas en débogage en mode mixte.  
  
- Vous avez essayé de modifier le code SQL Server.  
  
- Vous avez essayé de modifier le code lors du débogage d’un vidage Dr. Watson.  
  
- Vous avez essayé de modifier le code une fois qu’une exception non gérée s’est produite et que l’option «**dérouler la pile des appels sur les exceptions non gérées**» n’a pas été sélectionnée.  
  
- Vous avez essayé de modifier le code pendant le débogage d'une application d'exécution incorporée.  
  
- Vous avez essayé de modifier le code d’un programme auquel vous vous êtes attaché au lieu de démarrer à partir du menu **Déboguer** .  
  
- Vous avez essayé de modifier un code optimisé.  
  
- Vous avez essayé de modifier du code managé alors que la cible est une application 64 bits. Pour utiliser Modifier &amp; Continuer, vous devez affecter x86 à la cible. (*Project* **Propriétés**du projet, onglet **compiler** , paramètre de **compilateur avancé** .).  
  
- Vous avez tenté de modifier le code d'un assembly qui a été modifié pendant le débogage et a été rechargé.  
  
- Vous avez tenté de modifier le code d'un assembly qui n'a pas été chargé.  
  
- Vous avez commencé à déboguer une version ancienne de votre application (étant donné que la nouvelle version comporte des erreurs de build).  
  
- Vous avez tenté de modifier le code d'édition pendant son exécution.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **OK**  
 Fermez la boîte de dialogue et annulez la tentative de modification précédente.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications du code prises en charge (C++)](../debugger/supported-code-changes-cpp.md)
