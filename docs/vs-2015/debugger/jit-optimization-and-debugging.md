---
title: JIT optimisation et débogage | Microsoft Docs
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
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b4a0cf53dcc9870b5d0c93d2fcaaf2d942fd9959
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948910"
---
# <a name="jit-optimization-and-debugging"></a>Optimisation JIT et débogage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous déboguez une application managée, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] supprime l’optimisation du code de juste-à-temps (JIT) par défaut. La suppression de l'optimisation JIT signifie que vous déboguez un code non optimisé. Le code s'exécute un peu plus lentement parce qu'il n'est pas optimisé, mais votre expérience de débogage est beaucoup plus complète. Le débogage de code optimisé est plus ardu et est recommandé uniquement si vous rencontrez un bogue qui se produit dans un code optimisé mais ne peut pas être reproduit dans la version non optimisée.  
  
 L’optimisation JIT est contrôlée dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] par le **supprimer l’optimisation JIT lors du chargement du module** option. Vous pouvez trouver cette option sur le **général** page sous le **débogage** nœud dans le **Options** boîte de dialogue.  
  
 Si vous désactivez le **supprimer l’optimisation JIT lors du chargement du module** option, vous pouvez déboguer le code JIT optimisé, mais votre capacité de débogage peut être limitée car le code optimisé ne correspond pas le code source. Par conséquent, les fenêtres de débogage telles que la **variables locales** et **automatique** fenêtre ne peuvent pas afficher autant d’informations comme si vous déboguez un code non optimisé.  
  
 Une autre différence importante concerne le débogage avec Uniquement mon code. Si vous déboguez avec Uniquement mon code, le débogueur considère le code optimisé comme un code non-utilisateur, qui ne doit pas être affiché pendant le débogage. Par conséquent, si vous déboguez un code optimisé JIT, vous souhaiterez probablement désactiver Uniquement mon code. Pour plus d’informations, consultez [limiter le pas à pas à uniquement mon Code](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 N’oubliez pas que le **supprimer l’optimisation JIT lors du chargement du module** option supprime l’optimisation du code lorsque les modules sont chargés. Si vous rejoignez un processus déjà en cours d'exécution, il peut contenir un code qui est déjà chargé, compilé par JIT et optimisé. Le **supprimer l’optimisation JIT lors du chargement du module** option n’a aucun effet sur un tel code, bien qu’elle affecte des modules qui sont chargés après l’attachement. En outre, le **supprimer l’optimisation JIT lors du chargement du module** option n’affecte pas les modules, tels que WinForms.dll, qui sont créés avec NGEN.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)   
 [Attacher à des processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processus d'exécution managée](http://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
