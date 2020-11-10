---
title: Ensemble de règles des règles minimales managées pour le code managé
ms.date: 11/04/2016
description: En savoir plus sur l’ensemble de règles de règles minimales gérées dans Visual Studio, qui se concentre sur la sécurité, la robustesse et d’autres problèmes critiques. Consultez Description de la règle.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5a0e5c59621f948cbb7465a6726fa8c3003480d4
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435389"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Ensemble de règles des règles minimales managées pour le code managé

Les règles minimales gérées se concentrent sur les problèmes les plus critiques de votre code, y compris les failles de sécurité potentielles, les blocages d’application et d’autres erreurs de logique et de conception importantes. Incluez cet ensemble de règles dans n’importe quel ensemble de règles personnalisé que vous créez pour vos projets.

|Règle|Description|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Les types qui possèdent des champs supprimables doivent être supprimables|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Supprimez les finaliseurs vides|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Les champs pouvant être supprimés doivent l’être|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Surchargez l’opérateur égal lors du remplacement `ValueType.Equals`|
