---
title: Utiliser plusieurs comptes d’utilisateur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: b73c865c-74e0-420e-89cc-43524f4aafd0
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2f68328fb243c00c43c8ef454f10ad94c7d004a4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296786"
---
# <a name="work-with-multiple-user-accounts"></a>Utiliser plusieurs comptes d'utilisateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous avez plusieurs comptes Microsoft et/ou comptes professionnels ou scolaires, vous pouvez les ajouter à Visual Studio. Vous avez ainsi accès aux ressources de n'importe quel compte sans avoir à vous y connecter séparément. À compter de Visual Studio 2015 RTM, Azure, Application Insights, Team Foundation Server et Office 365 prennent en charge l'expérience de connexion simplifiée. D'autres services pourront être rajoutés au fil du temps.

 Après avoir ajouté plusieurs comptes sur un ordinateur, vous pourrez y accéder si vous vous connectez à Visual Studio sur un autre ordinateur. Il est important de noter que, bien que les noms de comptes soient itinérants, les informations d'identification ne le sont pas. Par conséquent, vous devrez entrer les informations d'identification de ces autres comptes la première fois que vous essayerez d'utiliser leurs ressources sur le nouvel ordinateur.

 Cette procédure pas à pas montre comment ajouter plusieurs comptes à Visual Studio et comment déterminer si les ressources accessibles à partir de ces comptes sont reflétées dans des endroits comme la boîte de dialogue **Ajouter un service connecté** , l' **Explorateur de serveurs**et **Team Explorer**.

#### <a name="sign-in-to-visual-studio"></a>Connectez-vous à Visual Studio

1. Connectez-vous à Visual Studio 2015 avec un compte Microsoft ou un compte professionnel. Votre nom d'utilisateur doit apparaître dans le coin supérieur droit de la fenêtre, comme ceci :

     ![Utilisateur actuellement utilisateur connecté](../ide/media/vs2015-username.png "VS2015_UserName")

### <a name="access-your-azure-account-in-server-explorer"></a>Accès à votre compte Azure dans l'Explorateur de serveurs
 Appuyez sur **Ctrl + Alt + S** pour ouvrir l' **Explorateur de serveurs**. Cliquez sur l'icône Azure pour la développer. Les ressources disponibles dans le compte Azure associé à l'ID que vous avez utilisé pour vous connecter à Visual Studio 2015 s'affichent alors. Les ressources affichées doivent ressembler à ceci, sauf qu’il doit s’agir de vos propres ressources et non des ressources de M. Guido :

 ![Explorateur de serveurs avec le nœud Azure Tools développé](../ide/media/vs2015-serverexplorer.png "VS2015_ServerExplorer")

 La première fois que vous utilisez Visual Studio sur un appareil spécifique, la boîte de dialogue affiche uniquement les abonnements inscrits sous l'ID avec lequel vous vous êtes connecté à l'IDE. Vous pouvez accéder aux ressources de n'importe lequel de vos autres comptes directement de l' **Explorateur de serveurs** en cliquant avec le bouton droit sur le nœud Azure, en choisissant **Gérer et filtrer les abonnements** , puis en ajoutant vos comptes à partir du contrôle de sélecteur de compte. Si vous le souhaitez, vous pouvez ensuite choisir un autre compte en cliquant sur la flèche déroulante vers le bas et en faisant une sélection dans la liste des comptes. Après avoir choisi le compte, vous pouvez choisir les abonnements inscrits sous ce compte que vous voulez afficher dans l'Explorateur de serveurs.

 ![Boîte de dialogue gérer les abonnements Azure](../ide/media/vs2015-manage-subs.png "vs2015_manage_subs")

 La prochaine fois que vous ouvrez l'Explorateur de serveurs, les ressources correspondant à ces abonnements s'affichent.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Accès à votre compte Azure via la boîte de dialogue Ajouter un service connecté

1. Créez un projet Application universelle en C#.

2. Cliquez avec le bouton droit sur le nœud du projet dans l’Explorateur de solutions, puis choisissez **Ajouter > Service connecté**. Dans l'Assistant lié à la fonctionnalité Ajouter un service connecté qui apparaît, vous pouvez voir la liste des services dans le compte Azure associé à votre ID de connexion Visual Studio. Notez que vous n'êtes pas obligé de vous connecter séparément à Azure. Vous devez néanmoins vous connecter aux autres comptes la première fois que vous tentez d'accéder à leurs ressources à partir d'un ordinateur donné.

    > [!WARNING]
    > S’il s’agit de la première fois que vous créez une application du Windows Store dans Visual Studio 2015 sur un ordinateur spécifique, vous êtes invité à activer votre appareil pour le mode de développement en accédant à **paramètres &#124; . Mises à jour et sécurité &#124; pour les développeurs** sur votre ordinateur. Pour plus d’informations, consultez [Activer votre appareil pour le développement](https://msdn.microsoft.com/library/windows/apps/dn706236.aspx).

### <a name="access_azure"></a> Accès à Azure Active Directory dans un projet web
 Azure AD permet de prendre en charge l'authentification unique des utilisateurs finaux dans les applications web MVC ASP.NET ou l'authentification AD dans les services API web. L'authentification de domaine est différente de l'authentification de comptes d'utilisateurs individuels ; les utilisateurs qui ont accès à votre domaine Active Directory peuvent utiliser leur compte Azure AD existant pour se connecter à vos applications web. Les applications Office 365 peuvent également utiliser l'authentification de domaine. Pour voir à quoi cela ressemble concrètement, créez une application web (**Fichier > Nouveau projet > C# > Cloud > Application web ASP.NET**). Dans la boîte de dialogue Nouveau projet ASP.NET, choisissez **Modifier l'authentification**. L'Assistant Authentification s'affiche et vous permet de choisir le type d'authentification à utiliser dans votre application.

 ![Boîte de dialogue Modifier l’authentification pour ASP.NET](../ide/media/vs2015-change-authentication.png "VS2015_change_authentication")

 Pour plus d’informations sur les différents types d’authentification dans ASP.NET, consultez [Creating ASP.NET Web Projects in Visual Studio 2013](https://docs.microsoft.com/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) (les informations relatives à l’authentification sont toujours applicables à Visual Studio 2015).

### <a name="access-your-visual-studio-team-services-account"></a>Accéder à votre compte Visual Studio Team Services
 Dans le menu principal, choisissez **Équipe > Se connecter à Team Foundation Server** pour afficher la fenêtre **Team Explorer**. Cliquez sur **Sélectionner les projets d’équipe**puis, dans la zone de liste sous **Sélectionner un serveur Team Foundation Server**, vous devriez voir l’URL de votre compte Visual Studio Team Services. Lorsque vous sélectionnez l'URL, vous êtes connecté sans avoir à entrer une nouvelle fois vos informations d'identification.

## <a name="add-a-second-user-account-to-visual-studio"></a>Ajouter un deuxième compte d'utilisateur à Visual Studio
 Cliquez sur la flèche bas à côté de votre nom d'utilisateur dans le coin supérieur droit de Visual Studio. Cliquez ensuite sur l'élément de menu **Paramètres du compte** . La boîte de dialogue **Gestionnaire de comptes** apparaît et affiche le compte avec lequel vous vous êtes connecté. Cliquez sur le lien **Ajouter un compte** dans l'angle inférieur gauche de la boîte de dialogue pour ajouter un nouveau compte Microsoft ou un nouveau compte professionnel ou scolaire.

 ![Sélecteur de compte Visual Studio](../ide/media/vs2015-acct-picker.png "VS2015_acct_picker")

 Suivez les instructions pour entrer les nouvelles informations d'identification du compte. L'illustration suivante montre le Gestionnaire de comptes après l'ajout du compte professionnel Contoso.com par un utilisateur.

 ![Gestionnaire de comptes](../ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Revisiter l'Assistant lié à la fonctionnalité Ajouter un service connecté et l'Explorateur de serveurs
 À présent, accédez de nouveau à l' **Explorateur de serveurs** , cliquez avec le bouton droit sur le nœud Azure, puis choisissez **Gérer et filtrer les abonnements**. Choisissez le nouveau compte en cliquant sur la flèche déroulante vers le bas située à côté du compte actif, puis choisissez les abonnements que vous voulez afficher dans l'Explorateur de serveurs. Tous les services associés à l'abonnement spécifié s'affichent alors. Même si vous n'êtes pas connecté à l'IDE de Visual Studio avec le deuxième compte, vous êtes connecté aux services et aux ressources de ce compte. Il en va de même pour **Projet > Ajouter un service connecté** et **Team > Se connecter à Team Foundation Server**.
