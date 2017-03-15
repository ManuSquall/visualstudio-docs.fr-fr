---
title: "CA1409&#160;: Les types visibles par COM doivent pouvoir &#234;tre cr&#233;&#233;s | Microsoft Docs"
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
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
helpviewer_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1409&#160;: Les types visibles par COM doivent pouvoir &#234;tre cr&#233;&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type référence marqué spécifiquement comme visible par des clients COM \(Component Object Model\) contient un constructeur public paramétrable, mais ne contient pas de constructeur public par défaut \(sans paramètre\).  
  
## Description de la règle  
 Un type sans constructeur public par défaut ne peut pas être créé par les clients COM.  Toutefois, le type reste accessible aux clients COM si un autre moyen est disponible pour créer le type et le passer au client ; par exemple, par le biais de la valeur de retour d'un appel de méthode.  
  
 La règle ignore les types qui sont dérivés de <xref:System.Delegate?displayProperty=fullName>.  
  
 Par défaut, les éléments suivants sont visibles par le modèle COM : assemblys, types publics, membres d'instances publics dans des types publics, et tous les membres de types valeur publics.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez un constructeur public par défaut ou supprimez le <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> du type.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si d'autres moyens sont fournis pour créer l'objet et le passer au client COM.  
  
## Règles connexes  
 [CA1017 : Marquer les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Voir aussi  
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)