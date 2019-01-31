---
title: Déverrouillage de Visual Studio 2015 | Microsoft Docs »
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8876cebf5851454aa3140f6a3269fa0d3ecbbc95
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774541"
---
# <a name="how-to-unlock-visual-studio"></a>Déverrouillage de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez évaluer Visual Studio gratuitement pendant 30 jours. Quand vous vous connectez à l'IDE, vous pouvez étendre la période d'évaluation de 90 jours. Pour continuer à utiliser Visual Studio, vous pouvez déverrouiller l'IDE en :

1.  utilisant un abonnement en ligne ;

2.  entrant une clé de produit.

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Pour déverrouiller Visual Studio à l'aide d'un abonnement en ligne
 Pour déverrouiller Visual Studio à l'aide d'un abonnement en ligne MSDN ou Visual Studio associé à un compte Microsoft ou à un compte professionnel ou scolaire :

1.  Cliquez sur le bouton « Connexion » en haut à droite de l'IDE (ou sélectionnez Fichier > Paramètres de compte pour ouvrir la boîte de dialogue Paramètres de compte et cliquez sur le bouton « Connexion »).

2.  Entrez les informations d'identification d'un compte Microsoft ou d'un compte professionnel ou scolaire. Visual Studio recherche un abonnement MSDN ou Visual Studio Team Services associé à votre compte.

> [!IMPORTANT]
>  Visual Studio recherche automatiquement les abonnements en ligne associés quand vous vous connectez à un compte Visual Studio Team Services à partir de la fenêtre d’outils Team Explorer. Quand vous vous connectez à un compte Visual Studio Team Services, vous pouvez utiliser un compte Microsoft ou un compte professionnel ou scolaire. Si un abonnement en ligne existe pour ce compte d'utilisateur, Visual Studio déverrouille automatiquement l'IDE.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>Pour déverrouiller Visual Studio avec une clé de produit

1.  Sélectionnez **Fichier > Paramètres de compte** pour ouvrir la boîte de dialogue Paramètres de compte, puis cliquez sur le lien « **Obtenir une licence avec une clé de produit** ».

2.  Entrez la clé de produit dans la zone fournie.

> [!TIP]
>  Les versions préliminaires de Visual Studio n'ont pas de clés de produit. Vous devez vous connecter à l'IDE pour utiliser les versions préliminaires.

## <a name="addressing-license-problem-states"></a>Corrections des problèmes d'état des licences

### <a name="updating-stale-licenses"></a>Mise à jour des licences obsolètes
 Le message ci-après selon lequel votre licence est périmée s'est peut-être affiché dans Visual Studio.

 ![Boîte de dialogue d’informations sur l’utilisateur de Visual Studio](../ide/media/vs2013-userinfo.png "VS2013_UserInfo")

 Ce message indique que, même si votre abonnement est peut-être toujours valide, le jeton de licence que Visual Studio utilise pour maintenir votre abonnement à jour n'a pas été actualisé et est devenu obsolète en raison de l'une des raisons suivantes :

1. Vous n'avez pas utilisé Visual Studio ou n'avez établi aucune connexion Internet pendant une longue période.

2. Vous vous êtes déconnecté de Visual Studio.

   Avant que le jeton de licence ne soit périmé, Visual Studio affiche un message d'avertissement vous invitant à entrer à nouveau vos informations d'identification.

   Si vous n'effectuez pas cette opération, le jeton entre en phase de péremption. Dans ce cas, la boîte de dialogue Paramètres du compte vous indique le nombre de jours avant que votre jeton n'arrive complètement à expiration. Une fois votre jeton arrivé à expiration, vous devez entrer à nouveau les informations d'identification de ce compte ou obtenir une licence avec une autre méthode mentionnée ci-dessus pour pouvoir continuer à utiliser Visual Studio.

> [!IMPORTANT]
>  Si vous utilisez Visual Studio pendant de longues périodes dans des environnements ayant un accès limité ou nul à Internet, vous devez utiliser une clé de produit pour déverrouiller Visual Studio afin d'éviter toute interruption.

### <a name="updating-expired-licenses"></a>Mise à jour des licences ayant expiré
 Si votre abonnement a expiré et vous n'avez plus accès à Visual Studio, vous devez :

1.  Renouveler votre abonnement. Pour plus d'informations sur la licence que vous utilisez, accédez à Fichier > boîte de dialogue Paramètres de compte et examinez les informations de licence sur le côté droit de la boîte de dialogue.

2.  Si un autre abonnement est associé à un compte différent, ajoutez ce compte à la liste Tous les comptes située à gauche de la boîte de dialogue Fichier > Paramètres de compte en cliquant sur le lien Ajouter un compte.

## <a name="see-also"></a>Voir aussi
 [Connexion à Visual Studio](../ide/signing-in-to-visual-studio.md)
