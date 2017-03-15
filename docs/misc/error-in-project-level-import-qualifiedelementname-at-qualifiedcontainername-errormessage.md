---
title: "Erreur dans l’importation au niveau du projet &#39;&lt;nom_qualifi&#233;_&#233;l&#233;ment&gt;&#39; &#224; &#39;&lt;nom_qualifi&#233;_conteneur&gt;&#39;&#160;: &lt;message_erreur&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC30797"
  - "vbc30797"
helpviewer_keywords: 
  - "BC30797"
ms.assetid: 529f354f-f255-4adc-ab21-bd1796e58d69
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Erreur dans l’importation au niveau du projet &#39;&lt;nom_qualifi&#233;_&#233;l&#233;ment&gt;&#39; &#224; &#39;&lt;nom_qualifi&#233;_conteneur&gt;&#39;&#160;: &lt;message_erreur&gt;
Une instruction accède à un élément de programmation défini dans un autre assembly, mais il n’existe aucune référence de projet à cet assembly.  
  
 Par exemple, votre code peut accéder à une énumération nommée `desiredEnumeration` à partir de la chaîne de qualification `otherNamespace.otherClass.desiredEnumeration`. Si le compilateur ne peut pas trouver `otherNamespace.otherClass` parmi les références de votre projet, il génère cette erreur.  
  
 **ID d’erreur :** BC30797  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que tous les éléments contenus dans la chaîne de qualification de l’élément de programmation sont correctement orthographiés.  
  
2.  Vérifiez que votre projet comporte une référence à l’assembly qui définit l’élément de programmation souhaité.  
  
3.  Consultez le message d’erreur et prenez les mesures nécessaires.  
  
## Voir aussi  
 [NOTINBUILD : Résolution d’une référence quand plusieurs variables portent le même nom](http://msdn.microsoft.com/fr-fr/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)