---
title: Ensemble de règles des règles de minimale managées pour le code managé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 83f8654a3cca246fa4853add231008e2fadbfc1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667912"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>Ensemble de règles des règles minimales managées pour le code managé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les règles minimales gérées se concentrent sur les problèmes les plus critiques de votre code, y compris les failles de sécurité potentielles, les blocages d’application et d’autres erreurs de logique et de conception importantes. Vous devez inclure cet ensemble de règles dans n’importe quel ensemble de règles personnalisé que vous créez pour vos projets.

|Règle|Description|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Les types qui possèdent des champs supprimables doivent être supprimables|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Supprimez les finaliseurs vides|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Les champs pouvant être supprimés doivent l’être|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals|
