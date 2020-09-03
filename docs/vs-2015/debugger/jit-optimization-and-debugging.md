---
title: Optimisation et débogage JIT | Microsoft Docs
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
ms.openlocfilehash: 56b010a01ccd7e40e696653e13dd7c972c97a9cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690541"
---
# <a name="jit-optimization-and-debugging"></a>Optimisation JIT et débogage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quand vous déboguez une application managée, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] supprime par défaut l’optimisation du code juste-à-temps (JIT). La suppression de l'optimisation JIT signifie que vous déboguez un code non optimisé. Le code s'exécute un peu plus lentement parce qu'il n'est pas optimisé, mais votre expérience de débogage est beaucoup plus complète. Le débogage de code optimisé est plus ardu et est recommandé uniquement si vous rencontrez un bogue qui se produit dans un code optimisé mais ne peut pas être reproduit dans la version non optimisée.  
  
 L’optimisation JIT est contrôlée [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] par l’option **Supprimer l’optimisation JIT lors du chargement du module** . Vous pouvez rechercher cette option sur la page **général** sous le nœud **débogage** de la boîte de dialogue **options** .  
  
 Si vous désactivez l’option **Supprimer l’optimisation JIT lors du chargement du module** , vous pouvez déboguer le code JIT optimisé, mais votre capacité de débogage peut être limitée, car le code optimisé ne correspond pas au code source. Par conséquent, les fenêtres du débogueur, telles que les fenêtres **variables locales** et **automatique** , peuvent ne pas afficher autant d’informations que possible si vous déboguez du code non optimisé.  
  
 Une autre différence importante concerne le débogage avec Uniquement mon code. Si vous déboguez avec Uniquement mon code, le débogueur considère le code optimisé comme un code non-utilisateur, qui ne doit pas être affiché pendant le débogage. Par conséquent, si vous déboguez un code optimisé JIT, vous souhaiterez probablement désactiver Uniquement mon code. Pour plus d’informations, consultez  [limiter le pas à pas à uniquement mon code](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 N’oubliez pas que l’option **Supprimer l’optimisation JIT lors du chargement du module** supprime l’optimisation du code lorsque les modules sont chargés. Si vous rejoignez un processus déjà en cours d'exécution, il peut contenir un code qui est déjà chargé, compilé par JIT et optimisé. L’option **Supprimer l’optimisation JIT lors du chargement du module** n’a aucun effet sur ce code, bien que cela affecte les modules qui sont chargés après l’attachement. En outre, l’option **Supprimer l’optimisation JIT lors du chargement du module** n’affecte pas les modules, tels que les WinForms.dll, qui sont créés avec Ngen.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de code managé](../debugger/debugging-managed-code.md)   
 [Navigation dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)   
 [Attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processus d’exécution managée](https://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
