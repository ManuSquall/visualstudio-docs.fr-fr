---
title: Déboguer un service WCF Self-Hosted | Microsoft Docs
Description: Découvrez comment déboguer un service WCF auto-hébergé. Le moyen le plus simple (mais pas toujours possible) consiste à configurer Visual Studio pour qu’il lance le client et le serveur.
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
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 983c053ca6bd1370cf67cb04eeb2626c2b1217aa
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398725"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Comment : déboguer un service WCF auto-hébergé
Un *service auto-hébergé* est un service WCF qui ne s’exécute pas à l’intérieur d’IIS, de l’hôte de service WCF ou du serveur de développement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Le moyen le plus simple de déboguer un WCF auto-hébergé consiste à configurer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour lancer à la fois le client et le serveur quand vous choisissez **Démarrer le débogage** dans le menu **Déboguer** .

 Si le service WCF est auto-hébergé dans ou dans un processus qui ne peut pas être lancé de cette manière, tel que le service NT, vous ne pouvez pas utiliser cette méthode. Au lieu de cela, vous pouvez effectuer l’une des opérations suivantes :

- Attachez manuellement le débogueur au processus d’hébergement. Pour plus d’informations, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

     — ou —

- Commencez à déboguer le client, puis exécutez un pas à pas détaillé dans un appel au service. Pour cela, vous devez activer le débogage dans le fichier app.config. Pour plus d’informations, [limitations sur le débogage WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-start-both-client-and-host-from-visual-studio"></a>Pour démarrer à la fois le client et l’hôte à partir de Visual Studio

1. Créez une [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solution qui contient à la fois les projets client et serveur.

2. Configurez la solution pour démarrer les processus du client et du serveur lorsque vous choisissez **Démarrer** dans le menu **Déboguer** .

   1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom de la solution.

   2. Cliquez sur **définir les projets de démarrage**.

   3. Dans la boîte de dialogue **\<name> Propriétés** de la solution, sélectionnez **plusieurs projets de démarrage**.

   4. Dans la grille **plusieurs projets de démarrage** , sur la ligne qui correspond au projet serveur, cliquez sur **action** , puis choisissez **Démarrer**.

   5. Sur la ligne qui correspond au projet client, cliquez sur **action** , puis choisissez **Démarrer**.

   6. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi
- [Débogage de services WCF](../debugger/debugging-wcf-services.md)
- [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md)
- [Comment : effectuer un pas à pas détaillé dans les services WCF](../debugger/how-to-step-into-wcf-services.md)