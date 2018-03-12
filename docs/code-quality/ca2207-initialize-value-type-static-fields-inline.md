---
title: "CA2207 : Initialisez les champs statiques de type valeur en ligne | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 248a43284dbdb376adaa3712f66b349f2fb6ca2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207 : Initialisez les champs static des types valeur en ligne
|||  
|-|-|  
|TypeName|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type valeur déclare un constructeur statique explicite.  
  
## <a name="rule-description"></a>Description de la règle  
 Lorsqu’un type valeur est déclaré, il subit une initialisation par défaut, tous les champs de type valeur sont définies à zéro et tous les champs de type référence étant `null` (`Nothing` en Visual Basic). Un constructeur statique explicite est garanti uniquement à exécuter avant le constructeur d’instance ou un membre statique de type est appelé. Par conséquent, si le type est créé sans appeler un constructeur d’instance, le constructeur statique n’est pas garanti qu’à exécuter.  
  
 Si toutes les données statiques sont initialisées inline et aucun constructeur statique explicite n’est déclaré, les compilateurs c# et Visual Basic ajoutent le `beforefieldinit` indicateur pour la définition de classe MSIL. Les compilateurs ajoutent également un constructeur statique privé qui contient le code d’initialisation statique. Ce constructeur statique privé est garanti avant d’accéder à tous les champs statiques de type.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle initialiser toutes les données statiques lorsqu’il est déclaré et supprimez le constructeur statique.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="related-rules"></a>Règles associées  
 [CA1810 : Initialisez les champs statiques de type référence en ligne](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)