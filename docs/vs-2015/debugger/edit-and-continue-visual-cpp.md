---
title: Modifier & Continuer (Visual C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3fd223b0a5891bc28cdef18dcd64312812607422
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62428462"
---
# <a name="edit-and-continue-visual-c"></a>Modifier & Continuer (Visual C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser Modifier et continuer dans les projets Visual C++. Consultez [modifications de Code prises en charge (C++)](../debugger/supported-code-changes-cpp.md) pour plus d’informations sur les limitations de modifier & Continuer.  
  
 À partir de Visual Studio 2015 Update 1, vous pouvez maintenant utiliser Modifier & Continuer dans les applications Windows Store C++ et DirectX, car il prend désormais en charge la **/Zi** commutateur de compilateur avec **/bigobj** basculer. Vous pouvez également utiliser Modifier & Continuer avec les fichiers binaires compilés avec la **/FASTLINK** basculer.  
  
 Parmi les autres améliorations d’Update 1 figurent une nouvelle boîte de dialogue d’attente annulable et l’affichage d’une notification quand un fichier ne prend pas en charge l’option Modifier et continuer. Pour plus d’informations sur les améliorations de mise à jour 1, consultez [améliorations pour C++ Modifier & Continuer dans Visual Studio 2015 Update 1](http://blogs.msdn.com/b/vcblog/archive/2015/11/30/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1.aspx).  
  
 L’option de compilateur [/Zo (Améliorer le débogage optimisé)](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) qui a été introduite dans Visual Studio 2013 Update 3 ajoute des informations aux fichiers de symboles (.pdb) pour les fichiers binaires compilés sans l’option [/Od (Désactiver (Débogage))](http://msdn.microsoft.com/library/aafb762y.aspx).  
  
 **/ Zo** désactive Modifier & Continuer. Voir [Guide pratique pour déboguer du code optimisé](../debugger/how-to-debug-optimized-code.md).  
  
## <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Activer ou désactiver Modifier & Continuer  
 Vous pouvez désactiver l’appel automatique de Modifier & Continuer si vous apportez des modifications au code que vous ne souhaitez pas appliquer tout de suite, pendant la session de débogage en cours. Vous pouvez également réactiver la fonctionnalité automatique Modifier & Continuer.  
  
1. Dans le menu **Outils** , choisissez **Options**.  
  
2. Dans la boîte de dialogue **Options** , sélectionnez **Débogage/Général**.  
  
3. Dans le groupe **Modifier &amp; Continuer** , cochez ou décochez la case **Activer Modifier et Continuer natif** .  
  
   La modification de ce paramètre s’applique à tous vos projets actuels. Après avoir modifié ce paramètre, il n'est pas nécessaire de régénérer l'application. Vous pouvez modifier ce paramètre pendant le débogage. Si vous générez l’application à partir de la ligne de commande ou d’un makefile, mais que vous effectuez le débogage dans l’environnement Visual Studio, vous pouvez continuer à utiliser Modifier & Continuer à condition de définir l’option **/ZI** .  
  
## <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Comment appliquer des modifications du code explicitement  
 Dans Visual C++, Modifier & Continuer peut appliquer des modifications de code de deux manières. Les modifications du code peuvent être implicitement appliquées, lorsque vous choisissez une commande d'exécution, ou explicitement, à l'aide de la commande **Appliquer les modifications du code** .  
  
 Lorsque vous appliquez des modifications du code de manière explicite, votre programme reste en mode arrêt - aucune exécution ne se produit.  
  
- Pour appliquer les modifications du code explicitement, dans le menu **Déboguer** , choisissez **Appliquer les modifications du code**.  
  
## <a name="BKMK_How_to_stop_code_changes"></a> Comment arrêter des modifications de code  
 Pendant que Modifier & Continuer est en train d'appliquer les modifications du code, vous pouvez arrêter l'opération.  
  
 Pour arrêter d'appliquer les modifications du code :  
  
- Dans le menu **Déboguer** , choisissez **Cesser d'appliquer les modifications du code**.  
  
  Cet élément de menu est visible uniquement lorsque les modifications du code sont appliquées.  
  
  Si vous choisissez cette option, aucune modification du code n'est validée.  
  
## <a name="BKMK_How_to_reset_the_point_of_execution"></a> Comment réinitialiser le point d'exécution  
 Certaines modifications du code peuvent entraîner le déplacement du point d'exécution vers un nouvel emplacement lorsque le mode Modifier & Continuer applique les modifications. Bien que Modifier & Continuer place le point d'exécution aussi précisément que possible, les résultats risquent d'être incorrects dans certains cas.  
  
 Dans Visual C++, une boîte de dialogue vous informe du déplacement du point d'exécution. Vérifiez que le nouvel emplacement est correct avant de poursuivre le débogage. S'il ne l'est pas, utilisez la commande **Définir l'instruction suivante** . Pour plus d’informations, consultez [Définir l’instruction suivante à exécuter](http://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
## <a name="BKMK_How_to_work_with_stale_code"></a> Comment utiliser du code périmé  
 Dans certains cas, Modifier & Continuer n'applique pas immédiatement les modifications du code au fichier exécutable, mais peut éventuellement les appliquer ultérieurement si vous poursuivez le débogage. Cela arrive si vous modifiez une fonction qui appelle la fonction actuelle ou si vous ajoutez plus de 64 octets de nouvelles variables à une fonction sur la pile des appels.  
  
 Dans ces cas, le débogueur continue à exécuter le code d’origine jusqu’à ce que les modifications puissent être appliquées. Le code périmé apparaît comme une fenêtre de fichier source temporaire dans une fenêtre source séparée, avec un titre comme `enc25.tmp`. La source modifiée continue à apparaître dans la fenêtre source d'origine. Si vous essayez de modifier le code périmé, un message d'avertissement apparaît.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de code prises en charge (C++)](../debugger/supported-code-changes-cpp.md)
