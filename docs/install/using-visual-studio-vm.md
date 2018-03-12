---
title: Utilisation de Visual Studio sur une machine virtuelle Azure | Microsoft Docs
description: "En savoir plus sur l’utilisation de Visual Studio sur une machine virtuelle Azure"
ms.date: 01/30/2018
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
ms.openlocfilehash: d8e99965867d5dbc2710d6c56c5b3dc90fc16dc8
ms.sourcegitcommit: 4b4027244b8de25e30b533148804b87321d3e8a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a id="top"> </a> Images Visual Studio sur Azure
L’utilisation de Visual Studio sur une machine virtuelle Azure préconfigurée est le moyen le plus simple et le plus rapide d’accéder à un environnement de développement opérationnel en partant de rien.  Des images du système avec différentes configurations de Visual Studio sont disponibles sur la [Place de marché Microsoft Azure](https://portal.azure.com/). Démarrez simplement une machine virtuelle et le tour est joué.

Vous découvrez Azure ? [Créez un compte Azure gratuit](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Quelles sont les configurations et les versions disponibles ?
Sur la Place de marché Microsoft Azure, vous trouverez des images des versions principales les plus récentes : Visual Studio 2017 et Visual Studio 2015.  Pour chaque version principale, la version d’origine (également appelée « RTW ») et les « dernières » versions mises à jour sont indiquées.  Pour chacune de ces versions, vous trouverez les éditions Visual Studio Enterprise et Visual Studio Community.  Nous mettons ces images à jour au moins une fois par mois afin d’inclure les dernières mises à jour de Visual Studio et Windows.  Bien que les noms des images ne changent pas, la description de chaque image inclut la version du produit installée et la date de « référence » de l’image.

|               Version commerciale              |        Éditions       |     Version du produit     |
|:------------------------------------------:|:---------------------:|:-----------------------:|
| Visual Studio 2017 - Dernière version (15.5) | Enterprise, Community |      Version 15.5.3     |
|         Visual Studio 2017 - RTW           | Enterprise, Community |      Version 15.0.7     |
|   Visual Studio 2015 - Dernière version (Update 3)   | Enterprise, Community |  Version 14.0.25431.01  |
|         Visual Studio 2015 - RTW           |         Aucun.          | (Expirée pour la maintenance) |

> [!NOTE]
> Conformément à la politique de Microsoft en matière de maintenance, la version d’origine (également appelée « RTW ») de Visual Studio 2015 a expiré en ce qui concerne la maintenance.  Par conséquent, Visual Studio 2015 Update 3 est la seule version restante proposée pour la ligne de produits Visual Studio 2015.

Pour plus d’informations, consultez [Politique de maintenance pour Visual Studio](https://www.visualstudio.com/en-us/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Quelles sont fonctionnalités installées ?
Chaque image contient l’ensemble de fonctionnalités recommandé pour cette édition de Visual Studio.  L’installation inclut généralement les éléments suivants :

* Toutes les charges de travail disponibles, y compris les composants facultatifs recommandés de cette charge de travail
* Kits SDK .NET 4.6.2 et .NET 4.7, packs de ciblage et outils de développement
* Visual F#
* Extension GitHub pour Visual Studio
* Outils LINQ to SQL

Il s’agit de la ligne de commande que nous utilisons pour installer Visual Studio durant la génération des images :

```
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

Si les images n’incluent pas la fonctionnalité de Visual Studio dont vous avez besoin, faites-nous-en part à l’aide de l’outil de commentaires (en haut à droite de la page).

## <a name="what-size-vm-should-i-choose"></a>Quelle taille de machine virtuelle dois-je choisir ?
Le provisionnement d’une nouvelle machine virtuelle est simple à réaliser, et Azure offre une gamme complète de tailles de machine virtuelle.  Comme avec tout achat de matériel, vous devez chercher le meilleur compromis entre coûts et performances.  Étant donné que Visual Studio est une puissante application multithread, il est préférable d’opter pour une taille de machine virtuelle incluant au moins 2 processeurs et 7 Go de mémoire. Dans Azure, cela se traduit, au minimum, par les tailles de machine virtuelle suivantes :

   * Standard_D2_v3
   * Standard_D2s_v3
   * Standard_D4_v3
   * Standard_D4s_v3
   * Standard_D2_v2
   * Standard_D2S_v2
   * Standard_D3_v2

Pour plus d’informations sur les dernières tailles de machine, consultez [Tailles des machines virtuelles Windows dans Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes).

Avec Azure, vous n’êtes pas limité à votre choix de départ : vous pouvez adapter ce choix en redimensionnant la machine virtuelle.  Vous pouvez provisionner une nouvelle machine virtuelle avec une taille plus appropriée ou redimensionner votre machine virtuelle existante sur un autre matériel sous-jacent.  Pour plus d'informations, consultez [Redimensionner une machine virtuelle Windows](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/resize-vm).

## <a name="after-i-get-the-vm-running-then-what"></a>Que dois-je faire après avoir mis en marche la machine virtuelle ?
Visual Studio suit le modèle BYOL (apportez votre propre licence) dans Azure.  Par conséquent, à l’instar d’une installation sur un matériel propriétaire, vous devez dans un premier temps introduire la licence de votre installation Visual Studio.  Vous pouvez déverrouiller Visual Studio en vous connectant à un compte Microsoft associé à un abonnement Visual Studio, ou en utilisant la clé de produit fournie avec votre achat initial.  Pour plus d’informations, consultez [Se connecter à Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/signing-in-to-visual-studio) et [Guide pratique pour déverrouiller Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-unlock-visual-studio).

## <a name="after-i-build-out-the-dev-vm-how-do-i-save-capture-it-for-future-or-team-use"></a>Après avoir créé la machine virtuelle de développement, comment puis-je l’enregistrer (la capturer) à des fins d’utilisation future ou de partage avec mon équipe ?

Le spectre des environnements de développement est immense, et il existe des coûts réels associés à la création d’environnements plus complexes.  Toutefois, quelle que soit la configuration de votre environnement, Azure permet de préserver facilement cet investissement en enregistrant/capturant votre machine virtuelle parfaitement configurée en tant qu’image de base pour une utilisation ultérieure, pour vous et/ou pour d’autres membres de votre équipe.  Par la suite, quand vous démarrerez une nouvelle machine virtuelle, vous pourrez la provisionner à partir de l’image de base au lieu de l’image Place de marché.

Pour résumer les étapes à suivre, vous devez exécuter sysprep et arrêter la machine virtuelle en cours d’exécution, puis *capturer (Figure 1)* la machine virtuelle en tant qu’image via l’interface utilisateur du portail Azure.  Azure enregistre le fichier `.vhd` qui contient l’image dans le compte de stockage de votre choix.  La nouvelle image apparaît ensuite comme une ressource image dans la liste des ressources de votre abonnement.

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*(Figure 1) Capture d’une image via l’interface utilisateur du portail Azure*</center>

Pour plus d’informations, consultez [Capturer la machine virtuelle dans l’image](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/capture-image-resource).

  **Rappel :** N’oubliez pas d’exécuter sysprep sur la machine virtuelle.  Si vous omettez cette étape, Azure ne peut pas configurer de machine virtuelle à partir de l’image.

> [!NOTE]
> Le stockage des images a un prix, mais ce coût incrémentiel est certainement insignifiant comparé aux frais de personnel qu’implique la récréation de la machine virtuelle depuis le début, pour chaque membre de votre équipe qui nécessite une machine virtuelle.  Par exemple, la création et le stockage pendant un mois d’une image de 127 Go réutilisable par tous les membres de votre équipe a un certain coût.  Mais ce coût est insignifiant comparé au nombre d’heures que chaque employé doit consacrer à créer et valider une zone de développement correctement configurée pour leur utilisation personnelle.

En outre, vos technologies ou tâches de développement peuvent nécessiter une nouvelle mise à l’échelle, pour mettre par exemple en place des configurations de développement variées ou des configurations de machines multiples.  Vous pouvez utiliser Azure DevTest Labs pour créer des _recettes_ permettant d’automatiser la création de votre « image idéale », ainsi que pour gérer les stratégies des machines virtuelles exécutées de votre équipe.  [Utiliser Azure DevTest Labs pour développeurs](https://docs.microsoft.com/en-us/azure/devtest-lab/devtest-lab-developer-lab) est la meilleure source d’informations pour en savoir plus sur DevTest Labs.

## <a name="next-steps"></a>Étapes suivantes
Maintenant que vous en savez un peu plus sur les images Visual Studio préconfigurées, l’étape suivante consiste à créer une machine virtuelle :

* [Créer une machine virtuelle avec le portail Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal)
* [Vue d’ensemble des machines virtuelles Windows](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/overview)
