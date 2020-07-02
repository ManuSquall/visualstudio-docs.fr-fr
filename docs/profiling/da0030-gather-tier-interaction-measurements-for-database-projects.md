---
title: DA0030-rassembler les mesures d’interaction de couche pour les projets de base de données | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 47ac30d4a1df36e72b8b12fa9aefb1b36aed6204
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544597"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030 : collecter les mesures d’interaction de couche pour les projets de base de données

|Élément|Valeur|
|-|-|
|ID de règle|DA0030|
|Category|Utilisation des outils de profilage|
|Méthode de profilage|échantillonnage|
|Message|La collecte des mesures d’interaction pour les applications multicouches vous aidera à comprendre les modèles d’utilisation de la base de données et les retards d’accès aux données de clé. Profilez de nouveau l’application en activant l’option Profilage d’interaction de couche.|
|Type de règle|Information|

## <a name="cause"></a>Cause
 Les appels aux méthodes <xref:System.Data> représentent une part importante des données de profilage et vous n’avez pas collecté de données d’interaction de couche lors de l’exécution du profilage. Effectuez un nouveau profilage et ajoutez des données d’interaction de couche.

## <a name="rule-description"></a>Description de la règle
 Cette règle se déclenche quand une activité importante est relevée dans les fonctions qui se trouvent dans les espaces de noms System.Data, notamment <xref:System.Data.Linq><xref:System.Data.Linq>.

 Les applications multicouches utilisent des services en couche pour leurs couches présentation et leur couches données. Souvent, la couche Données est un processus distinct qui exécute un système de gestion de base de données tel que Microsoft SQL Server. La couche données peut même être exécutée sur un ordinateur autre que celui de l’application. Les profils d’échantillonnage fournissent peu d’insight sur les fonctions et les services qui sont exécutés à distance ou hors processus.

 Les Outils de profilage peuvent collecter des informations de minutage pour les applications multicouches qui interagissent avec une couche Données Microsoft SQL Server à l’aide d’appels asynchrones aux services ADO.NET. Vous devez activer le profilage d’interaction de couche de manière explicite. En effet, ce profilage n’est pas activé par défaut.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Cette règle possède un caractère informatif et ne nécessite pas forcément d’action corrective.

 Pour plus d’informations sur l’ajout de données d’interaction de couche aux données de profilage à partir de l’IDE Visual Studio, consultez, [Collecte de données d’interaction de couche](../profiling/collecting-tier-interaction-data.md). Pour plus d’informations sur l’ajout de données d’interaction de couche à partir de la ligne de commande, consultez [Collecter les données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md).
