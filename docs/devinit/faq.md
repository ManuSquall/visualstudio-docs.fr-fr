---
title: Forum Aux Questions (FAQ)
description: Forum aux questions sur l’outil devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 98d61d86b894dc989e24aef809e0f97fd513f481
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932975"
---
# <a name="frequently-asked-questions-for-devinit"></a>Forum aux questions (FAQ) pour devinit

## <a name="is-devinit-just-for-github-codespaces"></a>Devinit est-il juste pour GitHub Codespaces ?

Pour le moment, devinit est disponible uniquement dans le cadre de la version bêta privée GitHub Codespaces. Toutefois, nous avons l’intention d’inclure des devinit dans une prochaine version de Visual Studio 2019.

## <a name="is-it-windows-only"></a>S’agit-il de Windows uniquement ?
Oui, devinit est axé sur la création d’environnements de développement qui fonctionnent pour les développeurs qui utilisent Visual Studio, ce qui signifie Windows. Nous envisageons d’autres plateformes, mais beaucoup d’entre elles disposent déjà de solutions exceptionnelles pour nous permettre de commencer avec Visual Studio et Windows.

## <a name="theres-no-tool-for-the-dependency-i-need"></a>Il n’y a pas d’outil pour la dépendance dont j’ai besoin !

Désolé, Si vous faites partie de la version bêta privée GitHub Codespaces, vous pouvez revenir à nous via le canal de commentaires pour la version bêta privée. Si vous n’êtes pas membre de la version bêta privée, nous aimerions tout de même vous faire part de vos commentaires et vous pouvez envoyer un problème sur notre [documentation sur Visual Studio](https://github.com/MicrosoftDocs/visualstudio-docs/) avec l’étiquette `devinit` pour demander un support pour l’outil dont vous avez besoin.

## <a name="something-went-wrong-how-do-i-debug"></a>Une erreur s’est produite, comment déboguer ?

Si devinit échoue, la première chose à essayer est l' `--verbose / -v` indicateur pour obtenir plus d’informations. L’outil sous-jacent appelé par devinit rencontre un problème. Les informations détaillées du journal doivent inclure une indication de l’emplacement suivant.

## <a name="why-not-just-a-script"></a>Pourquoi ne pas simplement être un script ?

La configuration d’environnements à l’aide d’un script est une technique d’ancienneté et peut fonctionner très bien. Si cela fonctionne pour vous, utilisez-le ! devinit est une autre option pour les développeurs lorsque les scripts ne sont pas le meilleur choix.

## <a name="why-not-a-container"></a>Pourquoi n’est-ce pas un conteneur ?

Les conteneurs, et Dockr, sont des outils formidables pour déployer un environnement via du code. Il existe plusieurs raisons pour lesquelles les conteneurs peuvent ne pas être la solution qui vous convient :

1. Si vous souhaitez utiliser un environnement de développement basé sur un bureau Windows.
1. Si vous disposez déjà d’un système d’exploitation et que vous souhaitez simplement le modifier au lieu de déployer un nouvel environnement.

Pour ces raisons, devinit est la personnalisation de l’environnement Windows dont vous disposez actuellement.

## <a name="what-about-other-vm-creation-tools-for-example-terraform-packer-chef-vagrant-etc"></a>Qu’en est-il des autres outils de création de machines virtuelles (par exemple, Terraform, Packer, chef, Vagrant, etc.)

Il existe un grand nombre d’outils exceptionnels pour créer des images Windows et vous devez les utiliser ! Toutefois, nous n’avons pas trouvé un qui remplissait tous les scénarios à l’esprit. Nous souhaitons que devinit soit un outil permettant aux développeurs de personnaliser leur environnement avec tout ce qui est nécessaire pour un référentiel particulier et de bénéficier d’une intégration parfaite avec Visual Studio, plutôt que d’être un outil de création d’images de machine virtuelle.

## <a name="what-about-winget"></a>Qu’en est-il de Winget ?

devinit n’est pas un gestionnaire de package comme Winget, et nous ne le souhaitons pas. Nous souhaitons que vous puissiez utiliser Winget avec devinit et nous travaillons sur un outil uniquement.

## <a name="how-are-restarts-handled"></a>Comment les redémarrages sont-ils gérés ?

Si une installation de devinit nécessite un redémarrage du système d’exploitation, un message d’erreur est généré sur la console. Vous devez ensuite redémarrer le système d’exploitation à un moment qui vous convient. Après le redémarrage, vous devrez peut-être réexécuter devinit si toutes les dépendances n’ont pas été installées.

## <a name="working-with-others"></a>Travailler avec d’autres utilisateurs

devinit consiste à activer l’utilisation de l’écosystème étendu pour déployer et configurer les dépendances que votre application peut avoir. Bien que devinit ait un avis sur ce qu’il fournit, devinit est essentiellement de permettre l’exécution d’autres outils à partir d’un fichier JSON déclaratif.

Aujourd’hui, devinit est tout simplement mis en route et notre [liste d’outils](devinit-tool-list.md) n’est qu’un début.
