---
title: "Avertissement du compilateur (niveau&#160;2) CS0728 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0728"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0728"
ms.assetid: ad6d860d-bac4-48f3-9eab-1efd2b6de6c0
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0728
Assignation potentiellement incorrecte à la 'variable' locale qui est l’argument d’une instruction using ou lock.  L’appel Dispose ou le déverrouillage se produira sur la valeur d’origine de la variable locale.  
  
 Il existe plusieurs scénarios où les blocs `using` ou `lock` provoquent une fuite temporaire de ressources. En voici un exemple :  
  
 `thisType f = null;`  
  
 `using (f)`  
  
 `{`  
  
 `f = new thisType();`  
  
 `...`  
  
 `}`  
  
 Dans ce cas, la valeur d’origine \(null\) de la variable `thisType` est supprimée à la fin de l’exécution du bloc `using`, mais l’objet `thisType` créé dans le bloc ne l’est pas, même s’il fait finalement l’objet d’une récupération de mémoire.  
  
 Pour résoudre cette erreur, utilisez la forme suivante .  
  
 `using (thisType f = new thisType())`  
  
 `{`  
  
 `...`  
  
 `}`  
  
 Dans ce cas, l’objet `thisType` nouvellement alloué est supprimé.  
  
## Exemple  
 Le code suivant génère l’erreur CS0728.  
  
```  
// CS0728.cs using System; public class ValidBase : IDisposable { public void Dispose() {  } } public class Logger { public static void dummy() { ValidBase vb = null; using (vb) { vb = null;  // CS0728 } vb = null; } public static void Main() { } }  
```