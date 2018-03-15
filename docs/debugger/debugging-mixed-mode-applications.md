---
title: "Déboguer les Applications en Mode mixte | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c67953db7daa9575fe30108f8772de550ed5b19d
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
---
# <a name="debugging-mixed-mode-applications"></a>Débogage des applications en mode mixte
Une application en mode mixte est une application qui combine du code natif (C++) avec du code managé (tel que Visual Basic, Visual C# ou C++ qui s'exécute sur le Common Language Runtime). Le débogage d'applications en mode mixte est largement transparent dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], il n'est pas très différent du débogage d'une application en mode unique. Quelques considérations spéciales sont toutefois à prendre en compte.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Permettre l'opération Modifier & Continuer pour C++ dans le cadre du débogage en mode mixte  

Pour activer Modifier & Continuer pour C++, consultez [comment activer et désactiver Modifier & Continuer](../debugger/how-to-enable-and-disable-edit-and-continue.md).

> [!NOTE]
> Pour pouvoir utiliser l'opération Modifier & Continuer pour C++ dans Visual Studio 2013, vous devez revenir au moteur de débogage hérité. Consultez [passage au Mode de compatibilité managé dans Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) sur le blog Microsoft Application Lifecycle Management.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Évaluation de propriété dans les applications en mode mixte  
 Dans une application en mode mixte, l'évaluation des propriétés par le débogueur est une opération coûteuse. Par conséquent, le débogage d'opérations telles que l'exécution pas à pas peut sembler lent. Pour plus d’informations, consultez [exécution pas à pas](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9). Si vos performances sont faibles lors du débogage en mode mixte, vous pouvez désactiver l'évaluation de propriété dans les fenêtres du débogueur.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
#### <a name="to-turn-off-property-evaluation"></a>Pour désactiver l'évaluation de propriété  
  
1.  Dans le menu **Outils** , choisissez **Options**.  
  
2.  Dans le **Options** boîte de dialogue, ouvrez le **débogage** dossier et sélectionnez le **général** catégorie.  
  
3.  Désactivez le **activer l’évaluation de la propriété et d’autres appels de fonction implicite** case à cocher.  
  
 Dans la mesure où les piles des appels natives et managées sont différentes, le débogueur ne peut pas toujours fournir la pile des appels complète pour le code mixte. Lorsque le code natif appelle le code managé, il est possible que vous notiez certaines divergences. Pour plus d’informations, consultez [Code mixte et informations manquantes dans la fenêtre Pile des appels](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)