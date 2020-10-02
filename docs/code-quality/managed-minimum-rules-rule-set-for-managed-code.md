---
title: Ensemble de règles des règles minimales managées pour le code managé
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 903b464172d541277de5fbac6d8ab035578b6154
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658501"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Ensemble de règles des règles minimales managées pour le code managé

Les règles minimales gérées se concentrent sur les problèmes les plus critiques de votre code, y compris les failles de sécurité potentielles, les blocages d’application et d’autres erreurs de logique et de conception importantes. Incluez cet ensemble de règles dans n’importe quel ensemble de règles personnalisé que vous créez pour vos projets.

|Règle|Description|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Les types qui possèdent des champs supprimables doivent être supprimables|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Supprimez les finaliseurs vides|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Les champs pouvant être supprimés doivent l’être|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Surchargez l’opérateur égal lors du remplacement `ValueType.Equals`|
