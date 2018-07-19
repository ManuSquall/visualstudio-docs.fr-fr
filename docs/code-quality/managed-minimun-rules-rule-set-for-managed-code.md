---
title: Règles de règles minimales managées défini pour le code managé
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 9803c5171cb15454e465253e410b3dc2f4e6215e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919050"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Règles de règles minimales managées défini pour le code managé
Les règles minimales gérées vous concentrer sur les problèmes les plus critiques dans votre code, notamment les failles de sécurité potentielles, application tombe en panne et d’autres erreurs de logique et de conception importantes. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets.

|Règle|Description|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Les types qui possèdent des champs supprimables doivent être supprimables|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Supprimez les finaliseurs vides|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Des champs supprimables doivent être supprimés.|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Surchargez l’opérateur equals en remplaçant ValueType.Equals|
