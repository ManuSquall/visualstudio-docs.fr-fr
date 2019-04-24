---
title: Limitations du débogage WCF | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34b69ac69c580fbd40278b5b7a0c9be26d672fa3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082020"
---
# <a name="limitations-on-wcf-debugging"></a>Limitations du débogage WCF
Il existe trois façons de commencer à déboguer un service WCF :

- Vous déboguez un processus client qui appelle un service. Le débogueur effectue un pas à pas détaillé dans le service. Le service n'a pas besoin d'être dans la même solution que votre application cliente.

- Vous déboguez un processus client qui fait une demande à un service. Le service doit faire partie de votre solution.

- Vous utilisez **Attacher au processus** pour effectuer un attachement à un service en cours d’exécution. Le débogage commence à l'intérieur du service.

  Cette rubrique décrit les limitations relatives à ces scénarios.

## <a name="limitations-on-stepping-into-a-service"></a>Limitations relatives au pas à pas détaillé dans un service
 Pour effectuer un pas à pas détaillé dans un service à partir d'une application cliente que vous déboguez, les conditions suivantes doivent être satisfaites :

- Le client doit appeler le service à l'aide d'un objet client synchrone.

- L'opération de contrat ne peut pas être unidirectionnelle.

- Si le serveur est asynchrone, vous ne pouvez pas afficher la pile des appels complète pendant que vous exécutez le code à l'intérieur du service.

- Le débogage doit être activé avec le code suivant dans le fichier app.config ou Web.config :

    ```xml
    <system.web>
      <compilation debug="true" />
    </system.web>
    ```

     Ce code ne doit être ajouté qu'une seule fois. Vous pouvez ajouter ce code en modifiant le fichier .config ou en effectuant un attachement au service à l’aide de **Attacher au processus**. Quand vous utilisez **Attacher au processus** sur un service, le code de débogage est ajouté automatiquement au fichier .config. Après quoi vous pouvez effectuer un débogage et un pas à pas détaillé dans le service sans avoir à modifier le fichier .config.

## <a name="limitations-on-stepping-out-of-a-service"></a>Limitations relatives au pas à pas sortant d'un service
 Un pas à pas sortant d'un service et un retour au client a les mêmes limitations que celles décrites pour un pas à pas détaillé dans un service. De plus, le débogueur doit être attaché au client. Si vous déboguez un client et effectuez un pas à pas dans un service, le débogueur reste attaché au service. C’est vrai si vous avez démarré le client à l’aide de **Démarrer le débogage** ou si vous avec effectué un attachement au client à l’aide de **Attacher au processus**. Si vous avez commencé le débogage par un attachement au service, le débogueur n'est pas encore attaché au client. Dans ce cas, si vous devez effectuer un pas à pas sortant du service et revenir au client, vous devez d’abord utiliser **Attacher au processus** pour effectuer l’attachement au client manuellement.

## <a name="limitations-on-automatic-attach-to-a-service"></a>Limitations relatives à l'attachement automatique à un service
 L'attachement automatique à un service a les limitations suivantes :

- Le service doit faire partie de la solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que vous déboguez.

- Le service doit être hébergé. Il peut faire partie d’un projet de site web (système de fichiers et HTTP), d’un projet d’application web (système de fichiers et HTTP) ou d’un projet Bibliothèque du service WCF. Les projets Bibliothèque du service WCF peuvent être des bibliothèques du service ou des bibliothèques du service de workflow.

- Le service doit être appelé à partir d'un client WCF.

- Le débogage doit être activé avec le code suivant dans le fichier app.config ou Web.config :

  ```xml
  <system.web>
    <compilation debug="true" />
  <system.web>
  ```

## <a name="self-hosting"></a>Auto-hébergement
 Un *service auto-hébergé* est un service WCF qui ne s’exécute pas à l’intérieur d’IIS, de l’hôte de service WCF ni du serveur de développement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Pour plus d’informations sur le débogage d’un service auto-hébergé, consultez [Comment : Déboguer un Service WCF auto-hébergé](../debugger/how-to-debug-a-self-hosted-wcf-service.md).

## <a name="self-hosting"></a>Auto-hébergement
 Pour permettre le débogage des applications [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 ou 3.5, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 ou 3.5 doit être installé avant que [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] soit installé. Si [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] est installé avant [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 ou 3.5, une erreur se produit quand vous essayez de déboguer une application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 ou 3.5. Le message d'erreur est « Impossible d'effectuer automatiquement un pas à pas détaillé sur le serveur ». Pour résoudre ce problème, utilisez le Windows **le panneau de configuration** > **programmes et fonctionnalités** pour réparer votre [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] installation.

## <a name="see-also"></a>Voir aussi
- [Débogage de services WCF](../debugger/debugging-wcf-services.md)
- [Guide pratique pour déboguer un service WCF auto-hébergé](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
