---
title: "L’espace de noms racine &lt;nom_espace_de_noms&gt; n’est pas conforme CLS | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40038"
  - "vbc40038"
helpviewer_keywords: 
  - "BC40038"
ms.assetid: ec850295-b2fe-4f19-b808-d22fe0aaa32d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’espace de noms racine &lt;nom_espace_de_noms&gt; n’est pas conforme CLS
Un assembly est marqué comme `<CLSCompliant(True)>`, mais le nom de l’espace de noms racine commence par un trait de soulignement \(`_`\).  
  
 Un élément de programmation peut contenir un ou plusieurs traits de soulignement, mais pour être conforme à la [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), il ne doit pas commencer par un trait de soulignement. Consultez [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
 Quand vous appliquez <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40038  
  
### Pour corriger cette erreur  
  
-   Si la conformité CLS est nécessaire, modifiez le nom de l’espace de noms racine pour qu’il ne commence pas par un trait de soulignement.  
  
-   Si le nom de l’espace de noms racine doit rester inchangé, supprimez <xref:System.CLSCompliantAttribute> de l’assembly ou marquez\-le comme `<CLSCompliant(False)>`.  
  
## Voir aussi  
 [Namespace Statement](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [Espaces de noms dans Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces)   
 [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace)   
 [NIB : Comment : modifier l’espace de noms pour une application \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/029d85c0-e173-4f7a-afba-a29f3aaf6ebf)   
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Visual Basic Naming Conventions](/dotnet/visual-basic/programming-guide/program-structure/naming-conventions)   
 [\<PAVE OVER\> Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)