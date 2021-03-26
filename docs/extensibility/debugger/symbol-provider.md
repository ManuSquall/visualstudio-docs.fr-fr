---
title: Fournisseur de symboles | Microsoft Docs
description: Découvrez les fournisseurs de symboles fournis par Visual Studio pour permettre à un évaluateur d’expression d’évaluer des variables et des expressions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 132e3c15eed86c9008e49b74b6da6e5da5a3ce33
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079382"
---
# <a name="symbol-provider"></a>Fournisseur de symboles
Une implémentation de l’évaluateur d’expression doit accéder aux informations de débogage symboliques générées par le compilateur de langage pour évaluer des variables et des expressions. Pour ce faire, il utilise les interfaces d’un fournisseur de symboles (SP), également appelé gestionnaire de symboles.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit des SPs pour le code managé, ainsi que du code natif utilisant le format de fichier de symboles de base de données du programme (PDB). À moins qu’il soit nécessaire que votre programme utilise des symboles stockés dans un format personnalisé, il est recommandé d’utiliser les SPs fournis par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Remarques relatives à l’implémentation
 Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] moteurs de débogage s’attendent à communiquer avec les SPS à l’aide d’interfaces CLR (Common Language Runtime). Par conséquent, un processeur de stockage qui fonctionne avec les moteurs de débogage Visual Studio doit prendre en charge le CLR. Une liste complète de toutes les interfaces de débogage CLR se trouve dans debugref.doc, qui fait partie de [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 Si votre SP ne fonctionne que avec votre moteur de débogage personnalisé, vous pouvez implémenter le SP comme vous le voyez en fonction des besoins de votre moteur de débogage.

## <a name="see-also"></a>Voir aussi
- [Composants du débogueur](../../extensibility/debugger/debugger-components.md)
