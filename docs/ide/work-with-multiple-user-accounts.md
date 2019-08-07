---
title: Utiliser plusieurs comptes d’utilisateur
ms.date: 07/23/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a49f7fe74977495c3e2a99e7311d4349ccd67bd
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483551"
---
# <a name="work-with-multiple-user-accounts"></a>Utiliser plusieurs comptes d’utilisateur

Si vous avez plusieurs comptes Microsoft et/ou comptes professionnels ou scolaires, vous pouvez les ajouter à Visual Studio. Vous avez ainsi accès aux ressources de n'importe quel compte sans avoir à vous y connecter séparément. Azure, Application Insights, Azure DevOps et les services Office 365 prennent tous en charge l’expérience de connexion simplifiée.

Une fois que vous aurez ajouté plusieurs comptes sur un ordinateur, vous pourrez y accéder en vous connectant à Visual Studio sur un autre ordinateur.

> [!NOTE]
> À la différence des noms de comptes, les informations d'identification ne sont pas itinérantes. Vous devrez les entrer pour ces autres comptes la première fois que vous essayerez d'utiliser leurs ressources sur un nouvel ordinateur.

Cet article explique comment ajouter plusieurs comptes à Visual Studio. Il montre également comment accéder aux ressources accessibles à partir de ces comptes dans des endroits comme la boîte de dialogue **Ajouter un service connecté**, **l’Explorateur de serveurs** et **Team Explorer**.

## <a name="sign-in-to-visual-studio"></a>Se connecter à Visual Studio

Connectez-vous à Visual Studio avec un compte Microsoft ou un compte professionnel. Votre nom d’utilisateur doit apparaître dans le coin supérieur de la fenêtre, comme ceci :

![Utilisateur actuellement connecté](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Accès à votre compte Azure dans l'Explorateur de serveurs

Appuyez sur **Ctrl**+**Alt**+**S** pour ouvrir **l’Explorateur de serveurs**. Développez le nœud **Azure**. Il contient les ressources disponibles dans le compte Azure associé au compte que vous avez utilisé pour vous connecter à Visual Studio, comme sur l’illustration suivante :

![Explorateur de serveurs avec nœud Azure développé](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

La première fois que vous utilisez Visual Studio sur un appareil spécifique, la boîte de dialogue affiche uniquement les abonnements inscrits sous le compte avec lequel vous avez ouvert une session. Vous pouvez accéder directement aux ressources de vos autres comptes dans **l’Explorateur de serveurs** en cliquant avec le bouton droit sur le nœud **Azure**, en choisissant **Gérer et filtrer les abonnements**, puis en ajoutant vos comptes avec le contrôle de sélecteur de compte. Si vous le souhaitez, vous pouvez ensuite choisir un autre compte en cliquant sur la flèche déroulante vers le bas et en faisant une sélection dans la liste des comptes. Après avoir choisi le compte, vous pouvez choisir les abonnements de ce compte à afficher dans **l’Explorateur de serveurs**.

![Boîte de dialogue Gérer les abonnements Azure](../ide/media/vs2015_manage_subs.png)

La prochaine fois que vous ouvrirez **l’Explorateur de serveurs**, les ressources associées à cet abonnement s’afficheront.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Accès à votre compte Azure via la boîte de dialogue Ajouter un service connecté

1. Ouvrez un projet existant ou créez-en un.

1. Choisissez le nœud du projet dans **l’Explorateur de solutions**, puis cliquez avec le bouton droit et choisissez **Ajouter** > **Service connecté**.

   L’Assistant **Ajouter un service connecté** qui apparaît présente la liste des services du compte Azure associé à votre compte de personnalisation Visual Studio. Il n’est pas nécessaire de se connecter séparément à Azure. Vous devez néanmoins vous connecter aux autres comptes la première fois que vous tentez d'accéder à leurs ressources sur un autre ordinateur.

### <a name="access-azure-active-directory-in-a-web-project"></a>Accès à Azure Active Directory dans un projet web

Azure Active Directory (AAD) prend en charge l'authentification unique des utilisateurs finaux dans les applications web MVC ASP.NET ou l'authentification AD dans les services API web. L’authentification d’un domaine est différente de l’authentification d’un compte utilisateur en particulier. Les utilisateurs qui ont accès à votre domaine Active Directory peuvent utiliser leur compte AAD pour se connecter à vos applications web. Les applications Office 365 peuvent également utiliser l'authentification de domaine.

::: moniker range="vs-2017"

Pour voir comment cela fonctionne, créez un projet **Application web ASP.NET Core**. Dans la boîte de dialogue **Nouvelle application web ASP.NET Core**, choisissez le modèle **Application web**, puis **Modifier l’authentification**.

::: moniker-end

::: moniker range=">=vs-2019"

Pour voir comment cela fonctionne, créez un projet **Application web ASP.NET Core**. Dans la boîte de dialogue **Créer une application web ASP.NET Core**, choisissez le modèle **Application web**, puis **Modifier** sous **Authentification**.

::: moniker-end

La boîte de dialogue **Modifier l’authentification** apparaît, où vous pouvez choisir le type d’authentification à utiliser dans votre application.

![Boîte de dialogue Modifier l'authentification pour ASP.NET](../ide/media/vs2015_change_authentication.png)

Pour plus d’informations sur les différents types d’authentification dans ASP.NET, consultez [Créer des projets web ASP.NET dans Visual Studio](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods).

### <a name="access-your-azure-devops-organization"></a>Accéder à une organisation Azure DevOps

Dans le menu principal, choisissez **Équipe** > **Gérer les connexions** pour ouvrir la fenêtre **Team Explorer – Se connecter**. Choisissez **Gérer les connexions** > **Se connecter à un projet**. Dans la boîte de dialogue **Se connecter à un projet**, sélectionnez un projet dans la liste (ou sélectionnez **Ajouter un serveur TFS** et entrez l’URL de votre serveur). Lorsque vous sélectionnez une URL, la connexion s’établit sans qu’il soit nécessaire d’entrer de nouveau les informations d'identification.

Pour plus d’informations, voir [Se connecter à des projets dans Team Explorer](connect-team-project.md).

## <a name="add-an-additional-account-to-visual-studio"></a>Ajouter un compte supplémentaire dans Visual Studio

Pour ajouter un compte supplémentaire dans Visual Studio :

1. Choisissez **Fichier** > **Paramètres du compte**.

1. Sous **Tous les comptes**, choisissez **Ajouter un compte**.

1. Sur la page **Connectez-vous à votre compte**, sélectionnez le compte ou choisissez **Utiliser un autre compte**. Suivez les instructions pour entrer les nouvelles informations d'identification du compte.

(Facultatif) Vous pouvez maintenant accéder à **l’Explorateur de serveurs** et voir les services Azure associés au compte que vous venez d’ajouter. Dans **l’Explorateur de serveurs**, cliquez avec le bouton droit sur le nœud **Azure**, puis choisissez **Gérer et filtrer les abonnements**. Choisissez le nouveau compte en cliquant sur la flèche déroulante vers le bas située à côté du compte actif, puis choisissez les abonnements que vous voulez afficher dans **l’Explorateur de serveurs**. Vous devez voir tous les services associés à l’abonnement spécifié. Même si vous n’avez pas ouvert de session Visual Studio avec le deuxième compte, la connexion est établie avec les services et les ressources de ce compte. Il en va de même pour **Projet** > **Ajouter un service connecté** et **Équipe** > **Se connecter à Team Foundation Server**.

### <a name="add-an-account-using-device-code-flow"></a>Ajouter un compte avec le flux de code d’appareil

Il peut arriver que vous ne puissiez pas vous connecter ou ajouter un compte en suivant la méthode classique. Cela peut se produire si Internet Explorer est bloqué pour une raison ou pour une autre, ou si votre réseau se trouve derrière un pare-feu. Pour contourner ce problème, vous pouvez activer le *flux de code d’appareil* afin d’ajouter un compte ou d’authentifier de nouveau votre compte. Le flux de code d’appareil permet de se connecter sur un autre navigateur ou un autre ordinateur &mdash; physique ou virtuel (machine virtuelle).

Pour vous connecter avec le flux de code d’appareil :

1. Ouvrez la page [**Comptes**](reference/accounts-environment-options-dialog-box.md) sous **Outils** > **Options** > **Environnement**, puis sélectionnez **Activer le flux de code d’appareil à l’ajout ou la réauthentification d’un compte**. Choisissez **OK** pour fermer les pages d’options.

1. Choisissez **Fichier** > **Paramètres des comptes** pour ouvrir la page de gestion des comptes.

1. Choisissez **Ajouter un compte** sous **Tous les comptes**.

   Une boîte de dialogue présente une URL et un code à coller dans un navigateur web.

   ![URL et code de flux de code d’appareil](media/work-with-multiple-user-accounts/device-login-code.png)

1. Appuyez sur **Ctrl**+**C** pour copier le texte de la boîte de dialogue, puis choisissez **OK** pour la fermer. Collez le texte que vous avez copié dans un éditeur de texte comme le Bloc-notes, pour pouvoir copier plus facilement le code à l’étape suivante.

1. Accédez à l’URL de connexion de l’appareil sur l’ordinateur ou le navigateur web que vous souhaitez utiliser pour vous connecter à Visual Studio, puis collez ou entrez le code que vous avez copié dans la zone intitulée **Code**.

   Le nom d’application **Visual Studio** devrait apparaître plus bas sur la page.

1. Sous **Visual Studio**, choisissez **Continuer**.

   ![device-login-page.png](media/work-with-multiple-user-accounts/device-login-page.png)

1. Suivez les instructions pour entrer les informations d'identification de votre compte.

   Une page s’affiche, vous indiquant que la connexion à Visual Studio est établie sur votre appareil, et que vous pouvez fermer la fenêtre du navigateur.

   ![Connexion à Visual Studio établie sur le navigateur](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. Revenez à la page de gestion des comptes dans Visual Studio : le nouveau compte apparaît sous **Tous les comptes**. Choisissez **Fermer**.

## <a name="see-also"></a>Voir aussi

- [Se connecter à Visual Studio](signing-in-to-visual-studio.md)
- [Se connecter à Visual Studio pour Mac](/visualstudio/mac/signing-in)
