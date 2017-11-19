---
title: "JIT optimisation et débogage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: acf75c0fbf6f5c3cfcf645d288c4e5e2eb2450d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="jit-optimization-and-debugging"></a>Optimisation JIT et débogage
Lorsque vous déboguez une application managée, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supprime l’optimisation du code de juste-à-temps (JIT) par défaut. La suppression de l'optimisation JIT signifie que vous déboguez un code non optimisé. Le code s'exécute un peu plus lentement parce qu'il n'est pas optimisé, mais votre expérience de débogage est beaucoup plus complète. Le débogage de code optimisé est plus ardu et est recommandé uniquement si vous rencontrez un bogue qui se produit dans un code optimisé mais ne peut pas être reproduit dans la version non optimisée.  
  
 L’optimisation JIT est contrôlée dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] par le **supprimer l’optimisation JIT lors du chargement du module** option. Vous pouvez rechercher cette option sur le **général** page sous le **débogage** nœud dans le **Options** boîte de dialogue.  
  
 Si vous désactivez le **supprimer l’optimisation JIT lors du chargement du module** option, vous pouvez déboguer le code JIT optimisé, mais votre capacité de débogage peut être limitée car le code optimisé ne correspond pas le code source. Par conséquent, les fenêtres de débogage telles que la **variables locales** et **automatique** fenêtre ne peuvent pas afficher autant d’informations comme si vous déboguez un code non optimisé.  
  
 Une autre différence importante concerne le débogage avec Uniquement mon code. Si vous déboguez avec Uniquement mon code, le débogueur considère le code optimisé comme un code non-utilisateur, qui ne doit pas être affiché pendant le débogage. Par conséquent, si vous déboguez un code optimisé JIT, vous souhaiterez probablement désactiver Uniquement mon code. Pour plus d’informations, consultez [limiter le pas à pas à uniquement mon Code](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 N’oubliez pas que le **supprimer l’optimisation JIT lors du chargement du module** option supprime l’optimisation du code lorsque les modules sont chargés. Si vous rejoignez un processus déjà en cours d'exécution, il peut contenir un code qui est déjà chargé, compilé par JIT et optimisé. Le **supprimer l’optimisation JIT lors du chargement du module** option n’a aucun effet sur un tel code, bien qu’elle affecte des modules qui sont chargés après l’attachement. En outre, le **supprimer l’optimisation JIT lors du chargement du module** option n’affecte pas les modules, tels que WinForms.dll, qui sont créés avec NGEN.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)   
 [Attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processus d'exécution managée](/dotnet/standard/managed-execution-process)