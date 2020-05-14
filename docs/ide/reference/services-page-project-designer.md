---
title: Services, page du Concepteur de projets
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d30d8e8ddcdc8c1fa4fe1935da1f1dedd1b18f4b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593562"
---
# <a name="services-page-project-designer"></a>Services, page du Concepteur de projets

Les services d’application cliente fournissent un accès simplifié aux services de connexion, de rôles et de profil [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] depuis les applications Windows Forms et WPF (Windows Presentation Foundation). Vous pouvez utiliser la page **Services** du **Concepteur de projets** pour activer et configurer les services d’application cliente pour votre projet.

Grâce aux services d’application cliente, vous pouvez utiliser un serveur centralisé pour authentifier les utilisateurs, déterminer le(s) rôle(s) assigné(s) à chaque utilisateur et stocker des paramètres d’application par utilisateur que vous pouvez partager sur le réseau. Pour plus d’informations, consultez [Services d’application cliente](/dotnet/framework/common-client-technologies/client-application-services).

Pour accéder à la page **Services**, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Quand le **Concepteur de projets** apparaît, cliquez sur l’onglet **Services**.

## <a name="task-list"></a>Liste des tâches

[Comment : configurer les services d'application cliente](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

 **Configuration**

Ce contrôle n’est pas modifiable dans cette page. Pour obtenir une description de ce contrôle, consultez [Compiler, page du Concepteur de projets (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) ou [Générer, page du Concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Plateforme**

Ce contrôle n’est pas modifiable dans cette page. Pour obtenir une description de ce contrôle, consultez [Compiler, page du Concepteur de projets (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) ou [Générer, page du Concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Activer les services d’application cliente**

Sélectionnez cette option pour activer les services d’application cliente. Vous devez spécifier des emplacements de service dans la page **Services** pour utiliser les services d’application cliente.

 **Utiliser l’authentification Windows**

Indique que le fournisseur d’authentification utilise l’authentification Windows, c’est-à-dire l’identité fournie par le système d’exploitation Windows.

 **Utiliser l’authentification par formulaire**

Indique que le fournisseur d’authentification utilise l’authentification par formulaire. Cela signifie que votre application doit fournir une interface utilisateur pour la connexion. Pour plus d’informations, consultez [Comment : implémenter la connexion utilisateur avec les services d’application cliente](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).

 **Emplacement du service d’authentification**

Utilisé uniquement avec l’authentification par formulaire. Spécifie l’emplacement du service d’authentification.

 **Facultatif : Fournisseur d’infos d’identification**

Utilisé uniquement avec l’authentification par formulaire. Indique l’implémentation <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> que le service d’authentification utilise pour afficher une boîte de dialogue de connexion quand votre application appelle la méthode `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> et passe des chaînes vides ou la valeur `null` pour les paramètres. Si vous ne renseignez pas cette zone, vous devez passer un nom d’utilisateur et un mot de passe valides à la méthode <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>. Vous devez spécifier le fournisseur d’informations d’identification sous la forme d’un nom de type qualifié d’assembly. Pour plus d’informations, consultez <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> et [Noms d’assemblys](/dotnet/framework/app-domains/assembly-names). Dans sa forme la plus simple, un nom de type qualifié d’assembly ressemble à l’exemple suivant : `MyNamespace.MyLoginClass, MyAssembly`

 **Emplacement des services de rôles**

Spécifie l’emplacement du service de rôles.

 **Emplacement des services de paramètres web**

Spécifie l’emplacement du service de profil (paramètres web).

 **Avancé**

Ouvre la [boîte de dialogue Paramètres avancés pour les services](../../ide/reference/advanced-settings-for-services-dialog-box.md), qui vous permet de substituer le comportement par défaut. Par exemple, vous pouvez utiliser cette boîte de dialogue afin de spécifier une base de données pour le stockage hors connexion au lieu d’utiliser le système de fichiers local. Pour plus d’informations, consultez [Paramètres avancés pour les services, boîte de dialogue](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Voir aussi

- [Services d’application cliente](/dotnet/framework/common-client-technologies/client-application-services)
- [Paramètres avancés pour les services, boîte de dialogue](../../ide/reference/advanced-settings-for-services-dialog-box.md)
- [Comment : configurer les services d'application cliente](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
- [Page Compiler, Concepteur de projets (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Générer, page du Concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md)
