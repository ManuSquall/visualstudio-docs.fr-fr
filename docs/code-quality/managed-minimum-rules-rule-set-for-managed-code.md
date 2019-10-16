---
title: Ensemble de règles des règles minimales managées pour le code managé
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1648f2aac0a0ace7f42ef923a0b26f6041204b27
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349580"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Ensemble de règles des règles minimales managées pour le code managé

Les règles minimales gérées se concentrent sur les problèmes les plus critiques de votre code, y compris les failles de sécurité potentielles, les blocages d’application et d’autres erreurs de logique et de conception importantes. Incluez cet ensemble de règles dans n’importe quel ensemble de règles personnalisé que vous créez pour vos projets.

|Règle|Description|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Les types qui possèdent des champs supprimables doivent être supprimables|
|[CA1821](../code-quality/ca1821.md)|Supprimez les finaliseurs vides|
|[CA2213](../code-quality/ca2213.md)|Les champs pouvant être supprimés doivent l’être|
|[CA2231](../code-quality/ca2231.md)|Surchargez l’opérateur égal lors de la substitution de `ValueType.Equals`|
