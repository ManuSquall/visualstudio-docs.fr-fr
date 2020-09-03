---
title: Services, page du Concepteur de projets | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 11e1cd997c76974e7b4b8771c0579c175469eca6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665487"
---
# <a name="services-page-project-designer"></a>Services, page du Concepteur de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les services d’application cliente fournissent un accès simplifié aux services de connexion, de rôles et de profil [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] depuis les applications Windows Forms et WPF (Windows Presentation Foundation). Vous pouvez utiliser la page **Services** du **Concepteur de projets** pour activer et configurer les services d’application cliente pour votre projet.

 Grâce aux services d’application cliente, vous pouvez utiliser un serveur centralisé pour authentifier les utilisateurs, déterminer le(s) rôle(s) assigné(s) à chaque utilisateur et stocker des paramètres d’application par utilisateur que vous pouvez partager sur le réseau. Pour plus d’informations, consultez [Services d’application cliente](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).

 Pour accéder à la page **Services**, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Quand le **Concepteur de projets** apparaît, cliquez sur l’onglet **Services**.

> [!NOTE]
> Les services d'application cliente nécessitent la version complète du .NET Framework et ne sont pas pris en charge dans le .NET Framework Client Profile. Si la case **Activer les services d’application cliente** est décochée, vérifiez que la liste **Framework cible** a la valeur .NET Framework 3.5 ou version ultérieure. Pour afficher le paramètre **Framework cible** en C#, ouvrez le Concepteur de projets, puis cliquez sur la page **Application**. Pour afficher le paramètre **Framework cible** en Visual Basic, ouvrez le Concepteur de projets, cliquez sur la page **Compiler**, puis sur **Options avancées de compilation**.

## <a name="task-list"></a>Liste des tâches
 [Comment : configurer les services d'application cliente](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur
 **Configuration** de Ce contrôle n’est pas modifiable dans cette page. Pour obtenir une description de ce contrôle, consultez [Compiler, page du Concepteur de projets (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) ou [Générer, page du Concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Plateforme** Ce contrôle n’est pas modifiable dans cette page. Pour obtenir une description de ce contrôle, consultez [Compiler, page du Concepteur de projets (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) ou [Générer, page du Concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Activer les services d’application cliente** Sélectionnez cette option pour activer les services d’application cliente. Vous devez spécifier des emplacements de service dans la page **Services** pour utiliser les services d’application cliente.

 **Utiliser l’authentification Windows** Indique que le fournisseur d’authentification utilisera l’authentification Windows, c’est-à-dire l’identité fournie par le système d’exploitation Windows.

 **Utiliser l’authentification par formulaire** Indique que le fournisseur d’authentification utilisera l’authentification par formulaire. Cela signifie que votre application doit fournir une interface utilisateur pour la connexion. Pour plus d’informations, consultez [Comment : implémenter la connexion utilisateur avec les services d’application cliente](https://msdn.microsoft.com/library/5431a671-eb02-4e18-a651-24764fccec9a).

 **Emplacement du service d’authentification** Utilisé uniquement avec l’authentification par formulaire. Spécifie l’emplacement du service d’authentification.

 **Facultatif : fournisseur d’informations d’identification** Utilisé uniquement avec l’authentification par formulaire. Indique l’implémentation <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> que le service d’authentification utilise pour afficher une boîte de dialogue de connexion quand votre application appelle la méthode `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> et passe des chaînes vides ou la valeur `null` pour les paramètres. Si vous ne renseignez pas cette zone, vous devez passer un nom d’utilisateur et un mot de passe valides à la méthode <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>. Vous devez spécifier le fournisseur d’informations d’identification sous la forme d’un nom de type qualifié d’assembly. Pour plus d’informations, consultez <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> et [Noms d’assemblys](https://msdn.microsoft.com/library/8f8c2c90-f15d-400e-87e7-a757e4f04d0e). Dans sa forme la plus simple, un nom de type qualifié d’assembly ressemble à l’exemple suivant : `MyNamespace.MyLoginClass, MyAssembly`

 **Emplacement du service de rôles** Spécifie l’emplacement du service de rôles.

 **Emplacement du service de paramètres Web** Spécifie l’emplacement du service de profil (paramètres Web).

 **Paramètres avancés** Ouvre la [boîte de dialogue Paramètres avancés pour les services](../../ide/reference/advanced-settings-for-services-dialog-box.md), que vous pouvez utiliser pour remplacer le comportement par défaut. Par exemple, vous pouvez utiliser cette boîte de dialogue afin de spécifier une base de données pour le stockage hors connexion au lieu d’utiliser le système de fichiers local. Pour plus d’informations, consultez [Paramètres avancés pour les services, boîte de dialogue](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Voir aussi
 [Client services d’application](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e) [Paramètres avancés pour les services, boîte de dialogue](../../ide/reference/advanced-settings-for-services-dialog-box.md) [comment : configurer le client services d’application](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8) [page compiler, concepteur de projets (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) [page générer, concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md) [Introduction au concepteur de projets](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)
