---
title: Utilisation de Visual Studio sur une machine virtuelle Azure
titleSuffix: ''
description: En savoir plus sur l’utilisation de Visual Studio sur une machine virtuelle Azure
ms.date: 11/17/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine
- installation
- visual studio
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 41247c13e8b35fd6e6cd26ac0ad0ea82f742fbb0
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306694"
---
# <a name="visual-studio-images-on-azure"></a>Images de Visual Studio sur Azure

L’exécution de Visual Studio sur une machine virtuelle Azure préconfigurée est un moyen simple et rapide de créer un environnement de développement opérationnel à partir de rien. Des images système avec différentes configurations de Visual Studio sont disponibles sur la [Place de Marché Azure](https://azuremarketplace.microsoft.com/marketplace/apps/category/compute?filters=virtual-machine-images%3Bmicrosoft%3Bwindows&page=1&subcategories=application-infrastructure).

Vous êtes un nouvel utilisateur d’Azure ? [Créer un compte Azure gratuit](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Quelles sont les configurations et les versions disponibles ?

La Place de Marché Azure met à disposition des images pour les dernières versions principales : Visual Studio 2019, Visual Studio 2017 et Visual Studio 2015.  Pour chaque version principale publiée figurent la version initialement publiée sur le web (RTW) et les versions mises à jour les plus récentes.  Pour chacune de ces versions, il existe des éditions Visual Studio Enterprise et Visual Studio Community.  Ces images sont actualisées au moins chaque mois pour inclure les dernières mises à jour Visual Studio et Windows.  Bien que les noms des images restent identiques, la description de chaque image inclut la version de produit installée et la date de création de l’image.

| Version commerciale                                                                                                                                                | Éditions              | Version du produit       |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|-----------------------|
| [Visual Studio 2019 : Version la plus récente (version 16.8)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019latest?tab=Overview) | Enterprise, Community | Version 16.8.0        |
| [Visual Studio 2019 : RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019?tab=Overview)                         | Entreprise            | Version 16.0.20       |
| [Visual Studio 2017 : Version la plus récente (15.9)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)           | Enterprise, Community | Version 15.9.29       |
| [Visual Studio 2017 : RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)                             | Enterprise, Community | Version 15.0.28       |
| [Visual Studio 2015 : Mise à jour la plus récente (Update 3)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)               | Enterprise, Community | Version 14.0.25431.01 |

> [!NOTE]
> Conformément à la politique de maintenance de Microsoft, la version initialement publiée (RTW) de Visual Studio 2015 a expiré pour la maintenance. Par conséquent, Visual Studio 2015 Update 3 est la seule version restante proposée pour la ligne de produits Visual Studio 2015.

Pour plus d’informations, consultez la [politique de maintenance de Visual Studio](/visualstudio/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Quelles sont les fonctionnalités installées ?

Chaque image contient le jeu de fonctionnalités recommandé pour cette édition de Visual Studio. En règle générale, l’installation comprend :

* Toutes les charges de travail disponibles, notamment les composants facultatifs recommandés de chaque charge de travail
* SDK .NET 4.6.2 et .NET 4.7, packs de ciblage et outils de développement
* Visual F#
* Extension GitHub pour Visual Studio
* Outils LINQ to SQL

Nous utilisons la ligne de commande suivante pour installer Visual Studio durant la génération des images :

```shell
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       --add Microsoft.Net.Component.4.7.SDK ^
       --add Microsoft.Net.Component.4.7.TargetingPack ^
       --add Microsoft.Net.Component.4.6.2.SDK ^
       --add Microsoft.Net.Component.4.6.2.TargetingPack ^
       --add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       --add Microsoft.VisualStudio.Component.FSharp ^
       --add Component.GitHub.VisualStudio ^
       --add Microsoft.VisualStudio.Component.LinqToSql
```

Si les images ne comprennent pas une fonctionnalité de Visual Studio dont vous avez besoin, faites-nous part de vos commentaires par le biais de l’outil de commentaires (en haut à droite de la page).

## <a name="what-size-vm-should-i-choose"></a>Quelle taille de machine virtuelle dois-je choisir ?

Azure offre une gamme complète de tailles de machine virtuelle. Visual Studio étant une application puissante et multithread, il faut une taille de machine virtuelle qui comprend au moins deux processeurs et 7 Go de mémoire. Voici les tailles de machines virtuelles recommandées pour les images Visual Studio :

* Standard_D2_v3
* Standard_D2s_v3
* Standard_D4_v3
* Standard_D4s_v3
* Standard_D2_v2
* Standard_D2S_v2
* Standard_D3_v2

Pour plus d’informations sur les tailles de machine les plus récentes, consultez [Tailles des machines virtuelles Windows dans Azure](/azure/virtual-machines/windows/sizes).

Avec Azure, vous pouvez rééquilibrer votre choix initial en redimensionnant la machine virtuelle. Vous pouvez soit provisionner une nouvelle machine virtuelle avec une taille plus appropriée, soit redimensionner votre machine virtuelle existante sur un autre matériel sous-jacent. Pour plus d’informations, consultez [Redimensionner une machine virtuelle Windows](/azure/virtual-machines/windows/resize-vm).

## <a name="after-the-vm-is-running-whats-next"></a>Une fois que la machine virtuelle est en cours d’exécution, que faire ?

Visual Studio suit le modèle BYOL (apportez votre propre licence) dans Azure. Comme pour une installation sur du matériel propriétaire, l’une des premières étapes est l’attribution d’une licence à votre installation Visual Studio. Pour déverrouiller Visual Studio, effectuez l’une des actions suivantes :

* Connectez-vous à l’aide d’un compte Microsoft associé à un abonnement Visual Studio.
* Déverrouillez Visual Studio à l’aide de la clé de produit fournie avec votre achat initial.

Pour plus d’informations, consultez [Se connecter à Visual Studio](../ide/signing-in-to-visual-studio.md) et [Guide pratique pour déverrouiller Visual Studio](../ide/how-to-unlock-visual-studio.md).

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Comment puis-je enregistrer la machine virtuelle de développement en vue d’une utilisation ultérieure ou par une équipe ?

Le spectre des environnements de développement est énorme, et la création d’environnements plus complexes a un coût réel. Quelle que soit la configuration de votre environnement, vous pouvez enregistrer (ou capturer) la machine virtuelle configurée en tant qu’« image de base » pour une utilisation ultérieure ou pour d’autres membres de votre équipe. Ensuite, quand vous démarrez une nouvelle machine virtuelle, vous pouvez l’approvisionner à partir de l’image de base au lieu de l’image de la Place de Marché Azure.

En bref : utilisez l’outil de préparation système (Sysprep) et arrêtez la machine virtuelle en cours d’exécution, puis capturez *(Figure 1)* la machine virtuelle en tant qu’image par le biais de l’interface utilisateur du portail Azure. Azure enregistre le fichier `.vhd` qui contient l’image dans le compte de stockage de votre choix. Ensuite, la nouvelle image apparaîtra en tant que ressource d’image dans la liste des ressources de votre abonnement.

![Capture d’une image via l’interface utilisateur du portail Azure](media/capture-vm.png)

*(Figure 1) Capturer une image par le biais de l’interface utilisateur du portail Azure.*

Pour plus d’informations, consultez [Créer une image managée d’une machine virtuelle généralisée dans Azure](/azure/virtual-machines/windows/capture-image-resource).

> [!IMPORTANT]
> N’oubliez pas d’utiliser Sysprep pour préparer la machine virtuelle. Si vous omettez cette étape, Azure ne peut pas provisionner une machine virtuelle à partir de l’image.

> [!NOTE]
> Des frais vous sont quand même facturés pour le stockage des images, mais ces frais incrémentiels seront probablement négligeables par rapport aux frais de personnel nécessaires pour régénérer la machine virtuelle à partir de rien, pour chaque membre de votre équipe ayant besoin d’une machine virtuelle. Par exemple, cela coûte quelques dollars de créer et de stocker pendant un mois une image de 127 Go réutilisable par tous les membres de votre équipe. Toutefois, ces coûts sont négligeables par rapport à toutes les heures investies par chaque employé pour créer et valider une zone de développement configurée correctement pour son usage individuel.

En outre, vos tâches de développement ou technologies peuvent nécessiter une mise à l’échelle (par exemple, différentes variétés de configurations de développement et plusieurs configurations d’ordinateurs). Vous pouvez utiliser Azure DevTest Labs pour créer des _recettes_ qui automatisent la construction de votre « image en or ». Vous pouvez également utiliser DevTest Labs pour gérer les stratégies des machines virtuelles en cours d’exécution pour votre équipe. [Utiliser Azure DevTest Labs pour développeurs](/azure/devtest-lab/devtest-lab-developer-lab) est la meilleure source pour obtenir plus d’informations sur DevTest Labs.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous en savez plus sur les images Visual Studio préconfigurées, l’étape suivante consiste à créer une machine virtuelle :

* [Créer une machine virtuelle avec le portail Azure](/azure/virtual-machines/windows/quick-create-portal)
* [Vue d’ensemble des machines virtuelles Windows](/azure/virtual-machines/windows/overview)
