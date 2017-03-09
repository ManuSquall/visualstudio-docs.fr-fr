---
title: "CA1413&#160;: &#201;viter les champs non publics dans les types valeur visibles par COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
helpviewer_keywords: 
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1413&#160;: &#201;viter les champs non publics dans les types valeur visibles par COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|  
|CheckId|CA1413|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type valeur qui est spécifiquement marqué comme visible par l'objet COM \(Component Object Model\) déclare un champ d'instance non public.  
  
## Description de la règle  
 Les champs d'instance non publics des types valeur visibles par COM sont visibles par les clients COM.  Passez en revue le contenu du champ pour voir les informations qui ne doivent pas être exposées, sinon vous aurez une conception imprévue ou des conséquences sur la sécurité.  
  
 Par défaut, tous les types valeur publics sont visibles par COM.  Cependant, pour réduire les faux positifs, cette règle nécessite de la visibilité COM du type à déclarer explicitement.  L'assembly conteneur doit être identifié par <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ayant la valeur `false` et le type doit être identifié par <xref:System.Runtime.InteropServices.ComVisibleAttribute> ayant la valeur `true`.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle et garder le champ masqué, remplacez le type valeur par un type référence ou supprimez l'attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> du type.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si l'exposition publique du champ est acceptable.  
  
## Exemple  
 L'exemple suivant présente un type qui enfreint la règle.  
  
 [!code-cs[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## Règles connexes  
 [CA1407 : Éviter les membres statiques dans les types visibles par COM](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017 : Marquer les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Voir aussi  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)