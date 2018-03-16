---
title: Utilisation de Visual Studio sur une machine virtuelle Azure | Microsoft Docs
description: "En savoir plus sur l’utilisation de Visual Studio sur une machine virtuelle Azure"
ms.date: 03/03/2018
ms.technology: vs-acquisition
ms.topic: article
helpviewer_keywords:
- azure services
- virtual machine; VM
- installation
- visual studio
author: PhilLee-MSFT
ms.author: phillee
manager: sacalla
ms.workload:
- multiple
ms.openlocfilehash: 4492a35c7d58aa92c2c3e86de5bd6be8f8ad9eca
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a id="top"> </a> Images Visual Studio sur Azure
L’utilisation de Visual Studio sur une machine virtuelle Azure préconfigurée est un moyen simple et rapide d’accéder à un environnement de développement opérationnel en partant de rien. Des images du système avec différentes configurations de Visual Studio sont disponibles sur la [Place de marché Microsoft Azure](https://azuremarketplace.microsoft.com/marketplace/apps?search=%22visual%20studio%202017%22&page=1).

Vous découvrez Azure ? [Créez un compte Azure gratuit](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Quelles sont les configurations et les versions disponibles ?
Sur la Place de marché Microsoft Azure, vous trouverez des images des versions principales les plus récentes : Visual Studio 2017 et Visual Studio 2015. Pour chaque version principale, la version (RTW) publiée d’origine et les versions mises à jour les plus récentes s’affichent. Chacune de ces versions propose les éditions Visual Studio Enterprise et Visual Studio Community. Ces images sont mises à jour au moins une fois par mois afin d’inclure les dernières mises à jour de Visual Studio et Windows. Bien que les noms des images ne changent pas, la description de chaque image inclut la version du produit installée et la date de « référence » de l’image.

| Version commerciale              | Éditions            | Version du produit     |
|:-----------------------------------------:|:----------------------------:|:-----------------------:|
| Visual Studio 2017 : Dernière version (15.6) |    Enterprise, Community     |      Version 15.6.0     |
|         Visual Studio 2017 : RTW           |    Enterprise, Community     |      Version 15.0.10    |
|   Visual Studio 2015 : Dernière version (Update 3)   |    Enterprise, Community     |  Version 14.0.25431.01  |
|         Visual Studio 2015 : RTW           |             Aucun.             | (Expirée pour la maintenance) |

> [!NOTE]
> Conformément à la politique de Microsoft en matière de maintenance, la version d’origine (RTW) de Visual Studio 2015 a expiré en ce qui concerne la maintenance. Visual Studio 2015 Update 3 est la seule version restante proposée pour la ligne de produits Visual Studio 2015.

Pour plus d’informations, consultez [Politique de maintenance pour Visual Studio](/visualstudio/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Quelles sont fonctionnalités installées ?
Chaque image contient l’ensemble de fonctionnalités recommandé pour cette édition de Visual Studio. L’installation inclut généralement les éléments suivants :

* Toutes les charges de travail disponibles, y compris les composants facultatifs recommandés de cette charge de travail
* Kits SDK .NET 4.6.2 et .NET 4.7, packs de ciblage et outils de développement
* Visual F#
* Extension GitHub pour Visual Studio
* Outils LINQ to SQL

Nous utilisons la ligne de commande suivante pour installer Visual Studio durant la génération des images :

```shell
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       add Microsoft.Net.Component.4.7.SDK ^
       add Microsoft.Net.Component.4.7.TargetingPack ^ 
       add Microsoft.Net.Component.4.6.2.SDK ^
       add Microsoft.Net.Component.4.6.2.TargetingPack ^
       add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       add Microsoft.VisualStudio.Component.FSharp ^
       add Component.GitHub.VisualStudio ^
       add Microsoft.VisualStudio.Component.LinqToSql
```

Si les images n’incluent pas la fonctionnalité de Visual Studio dont vous avez besoin, faites-nous-en part à l’aide de l’outil de commentaires dans l’angle supérieur droit de la page.

## <a name="what-size-vm-should-i-choose"></a>Quelle taille de machine virtuelle dois-je choisir ?
Azure offre une gamme complète de tailles de machine virtuelle. Étant donné que Visual Studio est une puissante application multithread, il est préférable d’opter pour une taille de machine virtuelle incluant au moins deux processeurs et 7 Go de mémoire. Nous recommandons les tailles de machine virtuelle suivantes pour les images de Visual Studio :

   * Standard_D2_v3
   * Standard_D2s_v3
   * Standard_D4_v3
   * Standard_D4s_v3
   * Standard_D2_v2
   * Standard_D2S_v2
   * Standard_D3_v2
    
Pour plus d’informations sur les dernières tailles de machine, consultez [Tailles des machines virtuelles Windows dans Azure](/azure/virtual-machines/windows/sizes).

Avec Azure, vous pouvez adapter ce choix en redimensionnant la machine virtuelle. Vous pouvez provisionner une nouvelle machine virtuelle avec une taille plus appropriée ou redimensionner votre machine virtuelle existante sur un autre matériel sous-jacent. Pour plus d’informations, consultez [Redimensionner une machine virtuelle Windows](/azure/virtual-machines/windows/resize-vm).

## <a name="after-the-vm-is-running-whats-next"></a>Une fois que la machine virtuelle est en cours d’exécution, que se passe-t-il ensuite ?
Visual Studio suit le modèle BYOL (apportez votre propre licence) dans Azure. À l’instar d’une installation sur un matériel propriétaire, vous devez dans un premier temps introduire la licence de votre installation Visual Studio. Pour déverrouiller Visual Studio, procédez de l’une des manières suivantes :
- Connectez-vous avec un compte Microsoft qui est associé à un abonnement Visual Studio 
- Déverrouillez Visual Studio avec la clé de produit fournie avec votre achat initial

Pour plus d’informations, consultez [Se connecter à Visual Studio](../ide/signing-in-to-visual-studio.md) et [Guide pratique pour déverrouiller Visual Studio](../ide/how-to-unlock-visual-studio.md).

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Comment puis-je enregistrer la machine virtuelle de développement à des fins d’utilisation future ou pour que l’équipe l’utilise ?

Le spectre des environnements de développement est immense, et il existe des coûts réels associés à la création d’environnements plus complexes. Quelle que soit la configuration de votre environnement, vous pouvez enregistrer, ou capturer, votre machine virtuelle configurée en tant « qu’image de base » pour une utilisation ultérieure ou pour d’autres membres de votre équipe. Par la suite, quand vous démarrerez une nouvelle machine virtuelle, vous pourrez la provisionner à partir de l’image de base au lieu de l’image Place de marché Azure.

Résumé rapide : utilisez l’outil Préparation du système (Sysprep) et arrêtez la machine virtuelle en cours d’exécution, puis capturez *(Figure 1)* la machine virtuelle en tant qu’image via l’interface utilisateur du portail Azure. Azure enregistre le fichier `.vhd` qui contient l’image dans le compte de stockage de votre choix. La nouvelle image apparaît ensuite comme une ressource image dans la liste des ressources de votre abonnement.

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*(Figure 1) Capture d’une image via l’interface utilisateur du portail Azure*</center>

Pour plus d’informations, consultez [Créer une image managée d’une machine virtuelle généralisée dans Azure](/azure/virtual-machines/windows/capture-image-resource).

> [!IMPORTANT]
> N’oubliez pas d’utiliser Sysprep pour préparer la machine virtuelle. Si vous omettez cette étape, Azure ne peut pas configurer de machine virtuelle à partir de l’image.

> [!NOTE]
> Le stockage des images a un prix, mais ce coût incrémentiel peut s’avérer insignifiant comparé aux frais de personnel qu’implique la récréation de la machine virtuelle depuis le début, pour chaque membre de votre équipe qui nécessite une machine virtuelle. Par exemple, la création et le stockage pendant un mois d’une image de 127 Go réutilisable par l’ensemble de votre équipe a un certain coût. Mais ce coût est insignifiant comparé au nombre d’heures que chaque employé doit consacrer à créer et valider une zone de développement correctement configurée pour leur utilisation personnelle.

En outre, vos technologies ou tâches de développement peuvent nécessiter une nouvelle mise à l’échelle, pour mettre par exemple en place des configurations de développement variées ou des configurations de machines multiples. Vous pouvez utiliser Azure DevTest Labs pour créer des _recettes_ permettant d’automatiser la création de votre « image idéale ». Vous pouvez également utiliser DevTest Labs pour gérer les stratégies des machines virtuelles exécutées de votre équipe. [Utiliser Azure DevTest Labs pour développeurs](/azure/devtest-lab/devtest-lab-developer-lab) est la meilleure source d’informations pour en savoir plus sur DevTest Labs.

## <a name="next-steps"></a>Étapes suivantes
Maintenant que vous en savez un peu plus sur les images Visual Studio préconfigurées, l’étape suivante consiste à créer une machine virtuelle :

* [Créer une machine virtuelle avec le portail Azure](/azure/virtual-machines/windows/quick-create-portal)
* [Vue d’ensemble des machines virtuelles Windows](/azure/virtual-machines/windows/overview)
