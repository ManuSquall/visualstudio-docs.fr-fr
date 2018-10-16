---
title: 'Comment : pas à pas détaillé des Services WCF | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 205dc10829227d2bb2f151687d7b4d4defbe03fe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184949"
---
# <a name="how-to-step-into-wcf-services"></a>Comment : effectuer un pas à pas détaillé dans les services WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], vous pouvez effectuer un pas à pas détaillé dans un service WCF. Si le service WCF est dans la même solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que le client, vous pouvez atteindre des points d'arrêt à l'intérieur du service WCF.  
  
 Pour que le pas à pas détaillé fonctionne, le débogage doit être activé dans le fichier app.config ou web.config. Pour plus d’informations sur la façon d’activer le débogage et pour connaître les limitations pas à pas détaillé dans les services WCF, consultez [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Pour effectuer un pas à pas détaillé dans un service WCF  
  
1.  Créez une solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui contient à la fois le client WCF et les projets de service WCF.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le projet de Client WCF, puis sélectionnez **définir comme projet de démarrage**.  
  
3.  Activez le débogage dans le fichier app.config ou web.config. Pour plus d’informations, consultez [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Dans le projet client, définissez un point d'arrêt à l'emplacement où vous souhaitez démarrer le pas à pas détaillé. En règle générale, cet emplacement précède directement l'appel de service WCF.  
  
5.  Lancez l'exécution jusqu'au point d'arrêt, puis démarrez le pas à pas détaillé. Le débogueur effectue automatiquement un pas à pas détaillé dans le service.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de Services WCF](../debugger/debugging-wcf-services.md)   
 [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Guide pratique pour déboguer un service WCF auto-hébergé](../debugger/how-to-debug-a-self-hosted-wcf-service.md)



