---
title: Effectuer un pas à pas détaillé dans les services WCF | Microsoft Docs
description: Effectuer un pas à pas détaillé dans un service Windows Communication Foundation (WCF). S’il se trouve dans la même solution Visual Studio que le client, appuyez sur des points d’arrêt dans le service WCF.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 428f5576b595797605abff2ebc5f4669e2927389
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150728"
---
# <a name="how-to-step-into-wcf-services"></a>Comment : effectuer un pas à pas détaillé dans les services WCF
Dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], vous pouvez effectuer un pas à pas détaillé dans un service WCF. Si le service WCF est dans la même solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que le client, vous pouvez atteindre des points d'arrêt à l'intérieur du service WCF.

 Pour que le pas à pas détaillé fonctionne, le débogage doit être activé dans le fichier app.config ou web.config. Pour plus d’informations sur l’activation du débogage et sur les limitations relatives au pas à pas détaillé dans les services WCF, consultez [limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-step-into-a-wcf-service"></a>Pour effectuer un pas à pas détaillé dans un service WCF

1. Créez une solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui contient à la fois le client WCF et les projets de service WCF.

2. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet de client WCF, puis cliquez sur **Définir comme projet de démarrage**.

3. Activez le débogage dans le fichier app.config ou web.config. Pour plus d’informations, consultez [limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md).

4. Dans le projet client, définissez un point d'arrêt à l'emplacement où vous souhaitez démarrer le pas à pas détaillé. En règle générale, cet emplacement précède directement l'appel de service WCF.

5. Lancez l'exécution jusqu'au point d'arrêt, puis démarrez le pas à pas détaillé. Le débogueur effectue automatiquement un pas à pas détaillé dans le service.

## <a name="see-also"></a>Voir aussi
- [Débogage de services WCF](../debugger/debugging-wcf-services.md)
- [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md)
- [Comment : déboguer un service Self-Hosted WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md)