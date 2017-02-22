---
title: "CA1011&#160;: Si possible, transmettez les types de base en tant que param&#232;tres | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ConsiderPassingBaseTypesAsParameters"
  - "CA1011"
helpviewer_keywords: 
  - "CA1011"
  - "ConsiderPassingBaseTypesAsParameters"
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1011&#160;: Si possible, transmettez les types de base en tant que param&#232;tres
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ConsiderPassingBaseTypesAsParameters|  
|CheckId|CA1011|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une déclaration de méthode comprend un paramètre formel qui constitue un type dérivé, et la méthode appelle seulement des membres du type de base du paramètre.  
  
## Description de la règle  
 Lorsqu'un type de base est spécifié en tant que paramètre dans une déclaration de méthode, tout type dérivé du type de base peut être passé en tant qu'argument correspondant à la méthode.  Lorsque l'argument est utilisé à l'intérieur du corps de méthode, la méthode spécifique exécutée dépend du type de l'argument.  Si les fonctionnalités supplémentaires fournies par le type dérivé ne sont pas requises, l'utilisation du type de base autorise une exploitation plus large de la méthode.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, changez le type du paramètre en son type de base.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle  
  
-   si la méthode requiert la fonctionnalité spécifique qui est fournie par le type dérivé  
  
     \- ou \-  
  
-   pour s'assurer que seul le type dérivé, ou un type plus dérivé, est passé à la méthode.  
  
 Dans ces cas, le code est plus fiable en raison de la vérification des types forts fournie par le compilateur et le moteur d'exécution.  
  
## Exemple  
 L'exemple suivant présente une méthode, `ManipulateFileStream`, qui ne peut être utilisée qu'avec un objet <xref:System.IO.FileStream> qui viole cette règle.  Une seconde méthode, `ManipulateAnyStream`, satisfait la règle en remplaçant le paramètre <xref:System.IO.FileStream> à l'aide d'un <xref:System.IO.Stream>.  
  
 [!code-cs[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]  
  
## Règles connexes  
 [CA1059 : Les membres ne doivent pas exposer certains types concrets](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)