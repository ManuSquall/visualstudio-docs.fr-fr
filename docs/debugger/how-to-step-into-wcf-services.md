---
title: "Comment : étape dans les Services WCF | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a67432767aaab23a96fbd4a9ca88e9735064c1df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-step-into-wcf-services"></a>Comment : effectuer un pas à pas détaillé dans les services WCF
Dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], vous pouvez effectuer un pas à pas détaillé dans un service WCF. Si le service WCF est dans la même solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que le client, vous pouvez atteindre des points d'arrêt à l'intérieur du service WCF.  
  
 Pour que le pas à pas détaillé fonctionne, le débogage doit être activé dans le fichier app.config ou web.config. Pour plus d’informations sur la façon d’activer le débogage et pour connaître les limitations pas à pas détaillé dans les services WCF, consultez [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Pour effectuer un pas à pas détaillé dans un service WCF  
  
1.  Créez une solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui contient à la fois le client WCF et les projets de service WCF.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le projet de Client WCF, puis **définir comme projet de démarrage**.  
  
3.  Activez le débogage dans le fichier app.config ou web.config. Pour plus d’informations, consultez [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Dans le projet client, définissez un point d'arrêt à l'emplacement où vous souhaitez démarrer le pas à pas détaillé. En règle générale, cet emplacement précède directement l'appel de service WCF.  
  
5.  Lancez l'exécution jusqu'au point d'arrêt, puis démarrez le pas à pas détaillé. Le débogueur effectue automatiquement un pas à pas détaillé dans le service.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de Services WCF](../debugger/debugging-wcf-services.md)   
 [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Guide pratique pour déboguer un service WCF auto-hébergé](../debugger/how-to-debug-a-self-hosted-wcf-service.md)