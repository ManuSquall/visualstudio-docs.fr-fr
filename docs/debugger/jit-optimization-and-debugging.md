---
title: "Optimisation JIT et d&#233;bogage | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "déboguer (Visual Studio), code optimisé"
  - "code optimisé, débogage"
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Optimisation JIT et d&#233;bogage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous déboguez une application managée, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supprime l'optimisation de code juste\-à\-temps \(JIT\) par défaut.  La suppression de l'optimisation JIT signifie que vous déboguez un code non optimisé.  Le code s'exécute un peu plus lentement parce qu'il n'est pas optimisé, mais votre expérience de débogage est beaucoup plus complète.  Le débogage de code optimisé est plus ardu et est recommandé uniquement si vous rencontrez un bogue qui se produit dans un code optimisé mais ne peut pas être reproduit dans la version non optimisée.  
  
 L'optimisation JIT est contrôlée dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] par l'option **Supprimer l'optimisation JIT lors du chargement du module**.  Vous pouvez rechercher cette option sur la page **Général** sous le nœud **Débogage** dans la boîte de dialogue **Options**.  
  
 Si vous effacez l'option **Supprimer l'optimisation JIT lors du chargement du module**, vous pouvez déboguer le code JIT optimisé, mais votre capacité de débogage peut être limitée car le code optimisé ne correspond pas au code source.  En conséquence, les fenêtres de débogage telles que **Variables locales** et la fenêtre **Automatique** ne peuvent pas afficher autant d'informations qu'elles le peuvent si vous déboguez un code non optimisé.  
  
 Une autre différence importante concerne le débogage avec Uniquement mon code.  Si vous déboguez avec Uniquement mon code, le débogueur considère le code optimisé comme un code non\-utilisateur, qui ne doit pas être affiché pendant le débogage.  Par conséquent, si vous déboguez un code optimisé JIT, vous souhaiterez probablement désactiver Uniquement mon code.  Pour plus d'informations, consultez [Limiter le pas à pas à Uniquement mon code](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Souvenez\-vous que l'option **Supprimer l'optimisation JIT lors du chargement du module** supprime l'optimisation du code lorsque les modules sont chargés.  Si vous rejoignez un processus déjà en cours d'exécution, il peut contenir un code qui est déjà chargé, compilé par JIT et optimisé.  L'option **Supprimer l'optimisation JIT lors du chargement du module** n'a aucun effet sur un tel code, bien qu'elle affecte des modules qui sont chargés après l'attachement.  De plus, l'option **Supprimer l'optimisation JIT lors du chargement du module** n'affecte pas les modules, tels que WinForms.dll, qui sont créés avec NGEN.  
  
## Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)   
 [Attacher aux processus en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processus d'exécution managée](../Topic/Managed%20Execution%20Process.md)