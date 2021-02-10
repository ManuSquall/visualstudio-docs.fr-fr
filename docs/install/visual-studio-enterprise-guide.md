---
title: Guide Visual Studio Enterprise
description: Configurez et dépannez Visual Studio dans un environnement d’entreprise.
ms.date: 07/29/2020
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e653d7ae5f2408fd8438cbdf69a28648c6bcc446
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967109"
---
# <a name="visual-studio-enterprise-guide"></a>Guide Visual Studio Enterprise
Si vous envisagez de gagner du temps lors de l’exécution de votre entreprise sur Visual Studio, commencez ici. Ce guide d’entreprise comprend des conseils qui peuvent vous aider à installer et à mettre à jour Visual Studio dans des scénarios d’entreprise courants, à être débloqués si vous rencontrez des problèmes et à signaler un problème si vous avez besoin d’une aide supplémentaire. 

## <a name="get-started"></a>Bien démarrer 
Découvrez comment déployer Visual Studio dans votre entreprise dans des environnements en réseau et hors connexion. 

- **Découvrez les options de déploiement d’entreprise dans les environnements en réseau**. Le [Guide de l’Administrateur Visual Studio](visual-studio-administrator-guide.md) fournit des conseils basés sur des scénarios pour les administrateurs système. 

- **[Recevez des conseils de dépannage](troubleshooting-installation-issues.md)**. Obtenez de l’aide lors de l’installation ou de la mise à jour de Visual Studio et découvrez comment signaler un problème si vous êtes bloqué. Ces conseils incluent des instructions pas à pas qui permettent de résoudre la plupart des problèmes d’installation en ligne ou hors connexion. 

- **[Créez une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)**. Si vous n’êtes pas connecté à Internet ou que vous disposez d’une connectivité Internet limitée, recherchez les options d’installation de Visual Studio. 

- **[Créer des packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md)**. Découvrez comment créer des packages de programme d’amorçage personnalisés en créant des manifestes de produit et de package. 

- **[Appliquer automatiquement des clés de produit lors du déploiement de Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)**. Vous pouvez appliquer votre clé de produit par programmation dans le cadre du script qui est utilisé pour automatiser le déploiement de Visual Studio. Vous pouvez définir une clé de produit sur un appareil par programmation, soit pendant l’installation de Visual Studio, soit à l’issue de l’installation. 

## <a name="install-visual-studio"></a>Installer Visual Studio 

Découvrez comment installer Visual Studio dans les scénarios d’entreprise courants. 

- **[Utilisez les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)**. Utilisez un grand nombre de paramètres pour contrôler ou personnaliser votre installation de Visual Studio. Automatisez le processus d’installation ou créez un cache des fichiers d’installation pour une utilisation ultérieure. 

- **Consultez [exemples de paramètres de ligne de commande pour l’installation de Visual Studio](command-line-parameter-examples.md)**. Pour illustrer l’utilisation des paramètres de ligne de commande pour installer Visual Studio, consultez plusieurs exemples que vous pouvez personnaliser en fonction de vos besoins. 

- **[Installer et utiliser Visual Studio et les services Azure derrière un pare-feu ou un serveur proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)**. Si votre organisation utilise des mesures de sécurité telles qu’un pare-feu ou un serveur proxy, il existe des URL de domaine que vous pouvez ajouter à une « liste verte », ainsi que des ports et des protocoles que vous pouvez ouvrir afin de bénéficier de la meilleure expérience possible lors de l’installation et de l’utilisation de Visual Studio et des services Azure. 

- **[Créer une installation réseau de Visual Studio](create-a-network-installation-of-visual-studio.md)**. Mettez en cache les fichiers pour l’installation initiale, ainsi que toutes les mises à jour du produit dans un dossier unique.  

## <a name="update-visual-studio"></a>Mettre à jour Visual Studio 2017 

Découvrez comment mettre à jour Visual Studio avec succès et résoudre les problèmes de mise à jour. 

- **[Mettre à jour une installation réseau de Visual Studio](update-a-network-installation-of-visual-studio.md)**. Mettez à jour une disposition d’installation réseau de Visual Studio avec les dernières mises à jour de produit afin qu’elles puissent être utilisées comme point d’installation pour la dernière mise à jour de Visual Studio, ainsi que pour gérer les installations déjà déployées sur les stations de travail clientes.

- **[Mettez à jour Visual Studio sur une ligne de base de maintenance](update-servicing-baseline.md)**. Comprendre la valeur de la mise à jour sur une ligne de base et découvrir la différence entre les versions mineures et les mises à jour de maintenance. 

- **[Mettez à jour Visual Studio à l’aide d’une disposition hors connexion minimale](update-minimal-layout.md)**. Pour les ordinateurs qui ne sont pas connectés à Internet, la création d’une disposition minimale est le moyen le plus simple et le plus rapide de mettre à jour vos instances de Visual Studio hors connexion.

- **[Réparez Visual Studio](repair-visual-studio.md) pour résoudre les problèmes de mise à jour**. Il peut arriver que votre installation Visual Studio soit endommagée ou corrompue. Une réparation est utile pour résoudre les problèmes d’installation dans toutes les opérations d’installation, y compris les mises à jour. 

- **Suivez les [lignes de base de sécurité Windows](/windows/security/threat-protection/windows-security-baselines)**. Microsoft s’engage à fournir à ses clients des systèmes d’exploitation sécurisés, tels que Windows 10 et Windows Server, et des applications sécurisées, telles que Microsoft Edge. Outre l’assurance de sécurité de ses produits, Microsoft vous permet également d’avoir un contrôle précis sur vos environnements en fournissant différentes fonctionnalités de configuration. 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi 

- [Guide de productivité pour Visual Studio](../ide/productivity-features.md)