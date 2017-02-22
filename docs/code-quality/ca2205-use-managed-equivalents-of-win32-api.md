---
title: "CA2205&#160;: Utilisez des &#233;quivalents manag&#233;s de l&#39;API Win32 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseManagedEquivalentsOfWin32Api"
  - "CA2205"
helpviewer_keywords: 
  - "CA2205"
  - "UseManagedEquivalentsOfWin32Api"
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2205&#160;: Utilisez des &#233;quivalents manag&#233;s de l&#39;API Win32
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseManagedEquivalentsOfWin32Api|  
|CheckId|CA2205|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode d'appel de code non managé est définie et une méthode dotée de la fonctionnalité équivalente existe dans la bibliothèque de classes du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Description de la règle  
 Une méthode d'appel de code non managé est utilisée pour appeler une fonction DLL non managée et est définie à l'aide de l'attribut <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>, ou du mot clé `Declare` en Visual Basic.  Une méthode d'appel de code non managé incorrectement définie peut engendrer des exceptions au moment de l'exécution du fait de problèmes tels qu'une fonction incorrectement nommée, un mappage erroné de types de données de valeurs de retour et de paramètres, et des spécifications de champs inexactes, notamment en termes de convention d'appel et de jeu de caractères.  Autant que faire se peut, appeler la méthode managée équivalente est généralement plus simple et moins propice aux erreurs que définir et appeler la méthode non managée directement.  L'appel à une méthode d'appel de code non managé peut également engendrer des problèmes de sécurité supplémentaires qui doivent être résolus.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, remplacez l'appel à la fonction non managée par un appel à son équivalent managé.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle si la méthode de remplacement suggérée ne fournit pas les fonctionnalités nécessaires.  
  
## Exemple  
 L'exemple suivant présente une définition de méthode d'appel de code non managé qui enfreint la règle.  Sont également présentés les appels à la méthode d'appel de code non managé ainsi que la méthode managée équivalente.  
  
 [!code-cs[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## Règles connexes  
 [CA1404 : Appeler GetLastError immédiatement après P\/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060 : Déplacer les P\/Invoke vers une classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400 : Des points d'entrée P\/Invoke doivent exister](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)  
  
 [CA1401 : Les P\/Invoke ne doivent pas être visibles](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)  
  
 [CA2101 : Spécifiez le marshaling pour les arguments de chaîne P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)