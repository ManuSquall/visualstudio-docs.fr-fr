---
title: 'Procédure : Déverrouiller Visual Studio'
titleSuffix: ''
ms.date: 03/30/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: fe0aa86be242e9a7e7ed8d877944c66247718167
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926303"
---
# <a name="how-to-unlock-visual-studio"></a>Procédure : Déverrouiller Visual Studio

Vous pouvez évaluer Visual Studio gratuitement pendant 30 jours. La connexion à l’environnement de développement intégré étend la période d’évaluation à 90 jours. Pour continuer à utiliser Visual Studio, déverrouillez l’IDE en effectuant l’une des opérations suivantes :

- en utilisant un abonnement en ligne

- en utilisant une clé de produit (Product Key)

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Pour déverrouiller Visual Studio à l'aide d'un abonnement en ligne

Pour déverrouiller Visual Studio avec un abonnement Visual Studio ou une organisation Azure DevOps associé à un compte Microsoft ou à un compte professionnel ou scolaire :

1. Choisissez le bouton **Connexion** en haut à droite de l’IDE (ou accédez à **Fichier** > **Paramètres du compte** pour ouvrir la boîte de dialogue **Paramètres du compte**, puis choisissez le bouton **Connexion**).

1. Entrez les informations d'identification d'un compte Microsoft ou d'un compte professionnel ou scolaire. Visual Studio recherche un abonnement Visual Studio ou une organisation Azure DevOps associé à votre compte.

> [!IMPORTANT]
> Visual Studio recherche automatiquement les abonnements en ligne associés quand vous vous connectez à une organisation Azure DevOps dans la fenêtre Outil **Team Explorer**. Vous pouvez alors utiliser un compte Microsoft ou un compte professionnel ou scolaire. Si un abonnement en ligne existe pour ce compte d'utilisateur, Visual Studio déverrouille automatiquement l'IDE.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>Pour déverrouiller Visual Studio avec une clé de produit

1. Sélectionnez **Fichier** > **Paramètres du compte** pour ouvrir la boîte de dialogue **Paramètres du compte**, puis choisissez le lien **Licence avec une clé de produit**.

1. Entrez la clé de produit dans la zone fournie.

> [!TIP]
> Les préversions de Visual Studio n’ont pas de clés de produit. Vous devez vous connecter à l’IDE pour utiliser les préversions.

## <a name="address-license-problem-states"></a>Corriger les problèmes d’état des licences

### <a name="update-stale-licenses"></a>Mettre à jour des licences obsolètes

Vous avez peut-être vu le message ci-après qui indique que votre licence est périmée dans Visual Studio. Il dit « Votre licence est périmée et doit être mise à jour ».

![Message d’expiration de licence Visual Studio](../ide/media/vs2017_stale-license.png)

Ce message indique que, même si votre abonnement est peut-être toujours valide, le jeton de licence que Visual Studio utilise pour maintenir votre abonnement à jour n’a pas été actualisé et est devenu obsolète en raison de l’une des raisons suivantes :

- Vous n’avez pas utilisé Visual Studio ou n’avez établi aucune connexion Internet pendant une longue période.
- Vous vous êtes déconnecté de Visual Studio.

Avant que le jeton de licence ne soit périmé, Visual Studio affiche un message d’avertissement qui vous demande d’entrer une nouvelle fois vos informations d’identification.

Si vous n’entrez pas à nouveau vos informations d’identification, l’expiration du jeton commence. De plus, la boîte de dialogue **Paramètres du compte** indique le nombre de jours restants avant l’expiration complète de votre jeton. Une fois votre jeton expiré, vous devez réentrer les informations d’identification de votre compte avant de pouvoir continuer à utiliser Visual Studio.

> [!Important]
> Si vous utilisez Visual Studio pendant de longues périodes dans des environnements ayant un accès limité ou nul à Internet, vous devez utiliser une clé de produit pour déverrouiller Visual Studio afin d’éviter toute interruption.

### <a name="update-expired-licenses"></a>Mettre à jour des licences ayant expiré

Si votre abonnement a expiré et que vous n’avez plus de droits d’accès à Visual Studio, vous devez renouveler votre abonnement ou ajouter un autre compte disposant d’un abonnement. Pour plus d’informations sur la licence utilisée, accédez à **Fichier** > **Paramètres du compte**, puis examinez les informations de licence situées sur le côté droit de la boîte de dialogue. Si vous avez un autre abonnement associé à un compte secondaire, ajoutez ce compte à la liste **Tous les comptes** à gauche de la boîte de dialogue en sélectionnant le lien **Ajouter un compte**.

## <a name="see-also"></a>Voir aussi

* [Se connecter à Visual Studio](../ide/signing-in-to-visual-studio.md)
