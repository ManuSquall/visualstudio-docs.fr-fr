---
title: Limitations du débogage WCF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b579712827033dab1556739f4ea79340232e761
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058521"
---
# <a name="limitations-on-wcf-debugging"></a>Limitations du débogage WCF
Il existe trois façons de commencer à déboguer un service WCF :  
  
-   Vous déboguez un processus client qui appelle un service. Le débogueur effectue un pas à pas détaillé dans le service. Le service n'a pas besoin d'être dans la même solution que votre application cliente.  
  
-   Vous déboguez un processus client qui fait une demande à un service. Le service doit faire partie de votre solution.  
  
-   Vous utilisez **attacher au processus** à attacher à un service qui est en cours d’exécution. Le débogage commence à l'intérieur du service.  
  
 Cette rubrique décrit les limitations relatives à ces scénarios.  
  
## <a name="limitations-on-stepping-into-a-service"></a>Limitations relatives au pas à pas détaillé dans un service  
 Pour effectuer un pas à pas détaillé dans un service à partir d'une application cliente que vous déboguez, les conditions suivantes doivent être satisfaites :  
  
-   Le client doit appeler le service à l'aide d'un objet client synchrone.  
  
-   L'opération de contrat ne peut pas être unidirectionnelle.  
  
-   Si le serveur est asynchrone, vous ne pouvez pas afficher la pile des appels complète pendant que vous exécutez le code à l'intérieur du service.  
  
-   Le débogage doit être activé avec le code suivant dans le fichier app.config ou Web.config :  
  
    ```xml
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     Ce code ne doit être ajouté qu'une seule fois. Vous pouvez ajouter ce code en modifiant le fichier .config ou en attachant au service à l’aide de **attacher au processus**. Lorsque vous utilisez **attacher au processus** sur un service, le code de débogage est automatiquement ajouté au fichier .config. Après quoi vous pouvez effectuer un débogage et un pas à pas détaillé dans le service sans avoir à modifier le fichier .config.  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>Limitations relatives au pas à pas sortant d'un service  
 Un pas à pas sortant d'un service et un retour au client a les mêmes limitations que celles décrites pour un pas à pas détaillé dans un service. De plus, le débogueur doit être attaché au client. Si vous déboguez un client et effectuez un pas à pas dans un service, le débogueur reste attaché au service. Cela est vrai si vous avez démarré le client à l’aide de **démarrer le débogage** ou attaché au client à l’aide de **attacher au processus**. Si vous avez commencé le débogage par un attachement au service, le débogueur n'est pas encore attaché au client. Dans ce cas, si vous avez à l’étape en provenance du service et au client, vous devez tout d’abord utiliser **attacher au processus** pour effectuer l’attachement au client manuellement.  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>Limitations relatives à l'attachement automatique à un service  
 L'attachement automatique à un service a les limitations suivantes :  
  
-   Le service doit faire partie de la solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que vous déboguez.  
  
-   Le service doit être hébergé. Il peut faire partie d’un projet de site web (système de fichiers et HTTP), d’un projet d’application Web (système de fichiers et HTTP) ou d’un projet Bibliothèque du service WCF. Les projets Bibliothèque du service WCF peuvent être des bibliothèques du service ou des bibliothèques du service de workflow.  
  
-   Le service doit être appelé à partir d'un client WCF.  
  
-   Le débogage doit être activé avec le code suivant dans le fichier app.config ou Web.config :  
  
    ```xml
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>Auto-hébergement  
 Un *service auto-hébergé* est un service WCF qui ne s’exécute pas à l’intérieur d’IIS, l’hôte de Service WCF, ou le [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] serveur de développement. Pour plus d’informations sur le débogage d’un service auto-hébergé, consultez [Comment : déboguer un Service de WCF auto-hébergé](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## <a name="self-hosting"></a>Auto-hébergement  
 Pour activer le débogage de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applications 3.0 ou 3.5, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 ou 3.5 doit être installé avant [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] est installé. Si [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] est installé avant [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 ou 3.5, une erreur se produit lorsque vous tentez de déboguer un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] application 3.0 ou 3.5. Le message d'erreur est « Impossible d'effectuer automatiquement un pas à pas détaillé sur le serveur ». Pour résoudre ce problème, utilisez le Windows **le panneau de configuration** > **programmes et fonctionnalités** pour réparer votre [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] installation.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de Services WCF](../debugger/debugging-wcf-services.md)   
 [Guide pratique pour déboguer un service WCF auto-hébergé](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
