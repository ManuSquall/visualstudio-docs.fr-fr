---
title: Ensemble de règles des règles minimales managées pour le code managé
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 56d8528a5a419eb23b1192ef265f70ea536cfe48
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890441"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Ensemble de règles des règles minimales managées pour le code managé

Les règles minimales gérées vous concentrer sur les problèmes les plus critiques dans votre code, notamment les failles de sécurité potentielles, les blocages d’application et les autres erreurs de logique et de conception importantes. Inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets.

|Règle|Description|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Les types qui possèdent des champs supprimables doivent être supprimables|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Supprimez les finaliseurs vides|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Champs supprimables doivent être supprimés.|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Surchargez l’opérateur equals en remplaçant ValueType.Equals|
