---
title: Sécurité pour les Solutions SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3febd2a9a3d2450740b08cac4ad8d3c891386c9a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42626131"
---
# <a name="security-for-sharepoint-solutions"></a>Sécurité pour les solutions SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] intègre les fonctionnalités suivantes pour vous aider à améliorer la sécurité des applications SharePoint.

## <a name="safe-control-entries"></a>Entrées de contrôle sécurisé
 Chaque élément de projet SharePoint créé dans [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] a un **entrées de contrôle sécurisé** collection de contrôles de propriété qui représente un coffre-fort. Son **Safe** sous-propriété vous permet de spécifier les contrôles que vous considérez comme sécurisés. Pour plus d’informations, consultez [fournissent des informations de déploiement du package et dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) et [spécifiant des composants WebPart sécurisés](http://go.microsoft.com/fwlink/?LinkId=177521).

## <a name="allowpartiallytrustedcallers-attribute"></a>Attribut AllowPartiallyTrustedCallers
 Par défaut, seules les applications qui sont totalement approuvées par le système de sécurité d’accès du code runtime peuvent accéder à un assembly de code managé partagé. Marquage d’un assembly entièrement fiable avec l’attribut AllowPartiallyTrustedCallers permet des assemblys de confiance partiel à y accéder.

 L’attribut AllowPartiallyTrustedCallers est ajouté à toute solution SharePoint qui n’est pas déployée dans le global assembly cache de système ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Cela inclut les solutions bac à sable ou solutions déployées au répertoire Bin de l’application SharePoint. Pour plus d’informations, consultez [modifications de sécurité Version 1 pour Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) et [déploiement de composants WebPart dans SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).

## <a name="safe-against-script-property"></a>Protégé contre les propriété de script
 *L’injection de script* est l’insertion de code potentiellement malveillant dans les contrôles ou des pages Web. Pour protéger les sites SharePoint 2010 contre l’injection de script, contributeurs ne peuvent pas afficher ou modifier des composants WebPart ou leurs propriétés par défaut. Ce comportement est contrôlé par un attribut SafeControl appelé SafeAgainstScript. Dans [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)], définissez cet attribut dans un élément de projet **entrées de contrôle sécurisé** sous-propriété **protégé contre les scripts**. Pour plus d’informations, consultez [fournissent des informations de déploiement du package et dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) et [Comment : marquer des contrôles comme des contrôles sécurisés](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Contrôle de compte d’utilisateur 7 Vista et Windows
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] et [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] intègrent une fonction de sécurité appelée en tant que le contrôle de compte utilisateur (UAC). Pour développer des solutions SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sur [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] et [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] systèmes, l’UAC exige que vous exécutez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en tant qu’un administrateur système. À partir de la **Démarrer** menu, ouvrez le menu contextuel pour [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], puis choisissez **exécuter en tant qu’administrateur**.

 Pour configurer le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] raccourci à toujours exécuter en tant qu’administrateur, ouvrez son menu contextuel, choisissez **propriétés**, choisissez le **avancé** situé dans le **propriétés**boîte de dialogue, puis le **exécuter en tant qu’administrateur** case à cocher.

 Pour plus d’informations, consultez [comprendre et configurer le contrôle de compte utilisateur dans Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). et [contrôle de compte d’utilisateur Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).

## <a name="sharepoint-permissions-considerations"></a>Considérations relatives à des autorisations SharePoint
 Pour développer des solutions SharePoint, vous devez disposer des autorisations suffisantes pour exécuter et déboguer des solutions SharePoint. Avant de pouvoir tester une solution SharePoint, procédez comme suit pour vous assurer que vous disposez des autorisations nécessaires :

1.  Ajoutez votre compte d’utilisateur en tant qu’administrateur sur le système.

2.  Ajoutez votre compte d’utilisateur en tant qu’un administrateur de batterie de serveurs pour le serveur SharePoint.

    1.  Dans Administration centrale de SharePoint 2010, choisissez le **gérer le groupe d’administrateurs de batterie de serveurs** lien.

    2.  Sur le **administrateurs de batterie** page, choisissez le **New** option de menu

3.  Ajoutez votre compte d’utilisateur pour au groupe WSS_ADMIN_WPG.

## <a name="additional-security-resources"></a>Autres ressources de sécurité
 Pour plus d’informations sur les problèmes de sécurité, consultez les rubriques suivantes.

### <a name="visual-studio-security"></a>sécurité (Visual Studio)

-   [Sécurité et autorisations utilisateur](http://go.microsoft.com/fwlink/?LinkId=177503)

-   [Sécurité dans le Code natif et .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)

-   [Sécurité dans le .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)

### <a name="sharepoint-security"></a>Sécurité SharePoint

-   [Sécurité et Administration de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177501)

-   [Centre de ressources de sécurité SharePoint](http://go.microsoft.com/fwlink/?LinkId=177498)

-   [Sécurisation des composants WebPart dans SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)

-   [Sécurité des applications Web amélioration : Menaces et contre-mesures](http://go.microsoft.com/fwlink/?LinkID=140080)

### <a name="general-security"></a>Sécurité générale

-   [MSDN Security Development Lifecycle](http://go.microsoft.com/fwlink/?LinkID=147149)

-   [Création d’Applications ASP.NET sécurisées : Authentification, autorisation et une Communication sécurisée](http://go.microsoft.com/fwlink/?LinkId=177494)

## <a name="see-also"></a>Voir aussi

- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)