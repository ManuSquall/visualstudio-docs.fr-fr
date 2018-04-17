---
title: 'CA2207 : Initialisez les champs statiques de type valeur en ligne | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5d063cda94451feef28aba9715033234d9adaa1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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