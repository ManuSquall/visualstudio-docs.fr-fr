---
title: Utiliser des comptes qui requièrent l’authentification multifacteur
ms.date: 05/27/2020
ms.custom: SEO-VS-2020
ms.topic: conceptual
description: Découvrez comment utiliser Visual Studio avec des comptes qui requièrent l’authentification multifacteur.
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9ac42ccff8c7bffcc22c453002aad1caf6935d28
ms.sourcegitcommit: e4630a3bb89b4d606fe2cbd709bc773c5b538b78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2021
ms.locfileid: "112975675"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>Comment utiliser Visual Studio avec des comptes qui requièrent l’authentification multifacteur

Quand vous collaborez avec des utilisateurs invités externes, il est judicieux de protéger vos applications et données avec des stratégies d' **accès conditionnel** telles que **l’authentification multifacteur (MFA)**.  

Une fois activées, les utilisateurs invités n’ont plus qu’un nom d’utilisateur et un mot de passe pour accéder à vos ressources, et doivent satisfaire des exigences de sécurité supplémentaires. Ces stratégies peuvent être appliquées au niveau du locataire, d’une application ou d’un utilisateur individuel invité, de la même façon qu’elles peuvent être activées pour les membres de votre propre organisation. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>Comment l’expérience Visual Studio est-elle affectée par les stratégies MFA ?
Les versions de Visual Studio antérieures à 16,6 peuvent avoir des expériences d’authentification dégradées lorsqu’elles sont utilisées avec des comptes qui ont activé des stratégies d’autorité de certification, telles que MFA, et qui sont associées à deux ou plusieurs locataires.

En raison de ces problèmes, votre instance de Visual Studio peut demander une réauthentification plusieurs fois par jour. Vous devrez peut-être entrer à nouveau vos informations d’identification pour les locataires précédemment authentifiés, même au cours de la même session Visual Studio.

## <a name="using-visual-studio-with-mfa-policies"></a>Utilisation de Visual Studio avec des stratégies MFA
Dans la version 16,6, nous avons ajouté de nouvelles fonctionnalités à Visual Studio 2019 qui simplifient la manière dont les utilisateurs peuvent accéder aux ressources sécurisées par le biais de stratégies d’autorité de certification, telles que MFA. Pour utiliser ce flux de travail amélioré, vous devez choisir d’utiliser le navigateur Web par défaut de votre système comme mécanisme d’ajout et de réauthentification des comptes Visual Studio.  

> [!WARNING]
> Le fait de ne pas utiliser ce flux de travail peut déclencher une dégradation de plusieurs invites d’authentification supplémentaires lors de l’ajout ou de la réauthentification de comptes Visual Studio. 

### <a name="enabling-system-web-browser"></a>Activation du navigateur Web système

> [!NOTE] 
> Pour une expérience optimale, nous vous recommandons de supprimer les données du navigateur Web par défaut de votre système avant de procéder à ce flux de travail. En outre, si vous avez des comptes professionnels ou scolaires dans vos paramètres Windows 10 sous **accès professionnel ou scolaire**, vérifiez qu’ils sont correctement authentifiés.

Pour activer ce flux de travail, accédez à la boîte de dialogue Options de Visual Studio **(outils > options...)**, sélectionnez l’onglet **comptes** , puis choisissez **navigateur Web système** sous la liste déroulante **Ajouter et réauthentifier les comptes à l’aide de :** . 

:::image type="content" source="media/select-system-web-browser.png" alt-text="Dans le menu, sélectionnez navigateur Web système.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>Connectez-vous à des comptes supplémentaires avec des stratégies MFA 
Une fois le flux de travail du navigateur Web système activé, vous pouvez vous connecter ou ajouter des comptes à Visual Studio comme vous le feriez normalement, via la boîte de dialogue Paramètres du compte **(fichier > les paramètres du compte...)**.   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Ajoutez un nouveau compte de personnalisation à Visual Studio." border="false":::

Cette action ouvre le navigateur Web par défaut de votre système, vous demande de vous connecter à votre compte et de valider toute stratégie d’authentification MFA requise.

Pendant le processus de connexion, vous pouvez recevoir une invite supplémentaire vous invitant à rester connecté. Cette invite s’affichera probablement la deuxième fois qu’un compte sera utilisé pour se connecter. Pour éviter de devoir entrer à nouveau vos informations d’identification, nous vous recommandons de sélectionner **Oui**, car cela garantit que vos informations d’identification sont conservées entre les sessions de navigateur.

:::image type="content" source="media/kmsi.png" alt-text="Rester connecté ?":::

En fonction de vos activités de développement et de la configuration des ressources, vous pouvez toujours être invité à entrer à nouveau vos informations d’identification pendant votre session. Cela peut se produire lorsque vous ajoutez une nouvelle ressource ou essayez d’accéder à une ressource sans avoir préalablement rempli ses exigences d’autorisation d’autorité de certification/authentification MFA.

## <a name="reauthenticating-an-account"></a>Réauthentification d’un compte  
En cas de problème avec votre compte, Visual Studio peut vous demander de saisir à nouveau vos informations d’identification de compte.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Réauthentifier votre compte Visual Studio.":::

En cliquant sur **réentrer vos informations d’identification** , vous ouvrez le navigateur Web par défaut de votre système et vous tentez d’actualiser automatiquement vos informations d’identification. En cas d’échec, vous êtes invité à vous connecter à votre compte et à valider toute stratégie d’autorité de certification/MFA requise.

> [!NOTE] 
> Pour une expérience optimale, gardez votre navigateur ouvert jusqu’à ce que toutes les stratégies d’autorité de certification/MFA soient validées pour vos ressources. La fermeture du navigateur peut entraîner la perte de l’État MFA précédemment créé et peut demander des invites d’autorisation supplémentaires.

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Comment refuser l’utilisation d’un locataire Azure Active Directory spécifique dans Visual Studio

Visual Studio 2019 version 16,6 offre la possibilité de filtrer les locataires individuellement ou globalement, en les hidding à partir de Visual Studio. Le filtrage élimine la nécessité de s’authentifier auprès de ce locataire, mais cela signifie également que vous ne pourrez pas accéder aux ressources associées.

Cette fonctionnalité est utile lorsque vous avez plusieurs locataires, mais que vous souhaitez optimiser votre environnement de développement en ciblant un sous-ensemble spécifique. Cela peut également vous aider dans les cas où vous ne pouvez pas valider une stratégie d’autorité de certification/MFA particulière, car vous pouvez filtrer le locataire incriminé. 

### <a name="how-to-filter-out-all-tenants"></a>Comment filtrer tous les locataires
Pour filtrer globalement tous les locataires, ouvrez la boîte de dialogue Paramètres du compte **(fichier > paramètres du compte...)** et décochez la case **authentifier sur tous les annuaires Azure active** .

Désélectionnez cette option pour vous assurer que vous vous authentifierez uniquement avec le locataire par défaut du compte. Cela signifie également que vous ne pouvez pas accéder à des ressources associées à d’autres locataires. votre compte peut être un invité sur.

### <a name="how-to-filter-out-individual-tenants"></a>Comment filtrer les clients individuels
Pour filtrer les locataires associés à votre compte Visual Studio, ouvrez la boîte de dialogue Paramètres du compte **(fichier > paramètres de compte...)** , puis cliquez sur **appliquer le filtre**. 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="Appliquer le filtre." border="false":::

La boîte de dialogue **filtrer le compte** s’affiche et vous permet de sélectionner les locataires que vous souhaitez utiliser avec votre compte. 

:::image type="content" source="media/select-filter-account.png" alt-text="Sélectionnez le compte à filtrer.":::

## <a name="see-also"></a>Voir aussi

- [Se connecter à Visual Studio](signing-in-to-visual-studio.md)
- [Se connecter à Visual Studio pour Mac](/visualstudio/mac/signing-in)
- [Utiliser plusieurs comptes d’utilisateur](work-with-multiple-user-accounts.md)
