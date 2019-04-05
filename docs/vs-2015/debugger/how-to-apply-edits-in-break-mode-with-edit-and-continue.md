---
title: 'Procédure : Appliquer des modifications en Mode arrêt avec modifier et continuer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd247cd50566130504110bd37c4b87f9e4783ae7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952856"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Procédure : Appliquer des modifications en Mode arrêt avec Modifier & Continuer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser Modifier &amp; Continuer pour modifier votre code en mode Arrêt, puis continuer sans arrêter et redémarrer l'exécution.  
  
 Modifier &amp; Continuer n'est pas disponible dans les scénarios de débogage suivants :  
  
-   Débogage en mode mixte (natif/managé).  
  
-   Débogage SQL.  
  
-   Débogage d’un dump Dr. Watson.  
  
-   Modification de code après une exception non gérée, lorsque l'option **Dérouler la pile des appels sur les exceptions non gérées** n'est pas sélectionnée.  
  
-   Débogage d'une application runtime incorporée.  
  
-   Débogage d’une application avec **attacher à** au lieu d’exécuter l’application avec **Démarrer** à partir de la **déboguer** menu.  
  
-   Débogage de code optimisé.  
  
-   Débogage de code managé lorsque la cible est une application 64 bits. Pour utiliser Modifier &amp; Continuer, vous devez affecter x86 à la cible. (_Projet_**propriétés**, **compiler** onglet, **paramètres avancés du compilateur** paramètre.).  
  
-   Débogage d'une version ancienne de votre code après un échec de génération par une nouvelle version en raison d'erreurs de build.  
  
### <a name="to-edit-code-in-break-mode"></a>Pour modifier du code en mode Arrêt  
  
1.  Passez en mode Arrêt en procédant de l'une des manières suivantes :  
  
    -   Définissez un point d’arrêt dans votre code, puis cliquez sur **Démarrer le débogage** dans le menu **Déboguer** et attendez que l’application parvienne au point d’arrêt.  
  
         – ou –  
  
    -   Démarrez le débogage, puis sélectionnez **Interrompre tout** dans le menu **Déboguer**.  
  
         – ou –  
  
    -   Lorsqu’une exception se produit, choisissez **activer la modification** sur le**Assistant Exception**.  
  
2.  Apportez toutes les modifications de code souhaitées et autorisées.  
  
     Pour plus d’informations, consultez [modifie non pris en charge dans Visual Basic Modifier & Continuer](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    >  Si vous tentez d'effectuer une modification du code qui n'est pas autorisée par l'opération Modifier &amp; Continuer, votre modification est soulignée d'un trait ondulé violet et une tâche s'affiche dans la liste des tâches. Il vous est impossible de continuer l'exécution du code sauf si vous annulez la modification de code non autorisée.  
  
3.  Dans le menu **Déboguer**, cliquez sur **Continuer** pour reprendre l’exécution.  
  
     Votre code s'exécute désormais avec les modifications que vous avez appliquées dans le projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Les modifications non prises en charge dans Visual Basic Modifier & Continuer](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Modifier & Continuer (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
