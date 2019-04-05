---
title: 'Procédure : Étape dans les Services WCF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0ad5ca2d74a1c141b9687d9b9eac5d8b3e268cc0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947219"
---
# <a name="how-to-step-into-wcf-services"></a>Procédure : Effectuer un pas à pas détaillé dans les services WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], vous pouvez effectuer un pas à pas détaillé dans un service WCF. Si le service WCF est dans la même solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que le client, vous pouvez atteindre des points d'arrêt à l'intérieur du service WCF.  
  
 Pour que le pas à pas détaillé fonctionne, le débogage doit être activé dans le fichier app.config ou web.config. Pour plus d’informations sur la façon d’activer le débogage et pour connaître les limitations pas à pas détaillé dans les services WCF, consultez [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Pour effectuer un pas à pas détaillé dans un service WCF  
  
1.  Créez une solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui contient à la fois le client WCF et les projets de service WCF.  
  
2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet de client WCF, puis cliquez sur **Définir comme projet de démarrage**.  
  
3.  Activez le débogage dans le fichier app.config ou web.config. Pour plus d’informations, consultez [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Dans le projet client, définissez un point d'arrêt à l'emplacement où vous souhaitez démarrer le pas à pas détaillé. En règle générale, cet emplacement précède directement l'appel de service WCF.  
  
5.  Lancez l'exécution jusqu'au point d'arrêt, puis démarrez le pas à pas détaillé. Le débogueur effectue automatiquement un pas à pas détaillé dans le service.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de services WCF](../debugger/debugging-wcf-services.md)   
 [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Guide pratique pour déboguer un service WCF auto-hébergé](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
