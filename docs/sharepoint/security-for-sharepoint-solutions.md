---
title: Sécurité pour les solutions SharePoint | Microsoft Docs
description: Découvrez les fonctionnalités de Visual Studio qui permettent d’améliorer la sécurité des applications SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 588b2af3672851bf7f452287d8383aa2d319347d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881579"
---
# <a name="security-for-sharepoint-solutions"></a>Sécurité pour les solutions SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] intègre les fonctionnalités suivantes pour aider à améliorer la sécurité des applications SharePoint.

## <a name="safe-control-entries"></a>Entrées de contrôle sécurisé
 Chaque élément de projet SharePoint créé dans [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] a une propriété **entrées de contrôle sécurisé** qui représente une collection de contrôles sécurisés. Sa sous-propriété **Safe** vous permet de spécifier les contrôles que vous envisagez de sécuriser. Pour plus d’informations, consultez fournir des informations sur le [package et le déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) et [spécification de WebParts sécurisés](/previous-versions/office/developer/sharepoint2003/dd583154(v=office.11)#specifying-safe-web-parts).

## <a name="allowpartiallytrustedcallers-attribute"></a>attribut AllowPartiallyTrustedCallers
 Par défaut, seules les applications entièrement approuvées par le système de sécurité d’accès du code (CAS) du Runtime peuvent accéder à un assembly de code managé partagé. Le marquage d’un assembly avec un niveau de confiance suffisant avec l’attribut AllowPartiallyTrustedCallers permet aux assemblys de confiance partielle d’y accéder.

 L’attribut AllowPartiallyTrustedCallers est ajouté à toute solution SharePoint qui n’est pas déployée sur le système Global Assembly Cache ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] ). Cela comprend les solutions ou les solutions bac à sable (sandbox) déployées dans le répertoire bin de l’application SharePoint. Pour plus d’informations, consultez [modifications de sécurité de la version 1 pour le Microsoft .NET Framework](/previous-versions/msp-n-p/ff921345(v=pandp.10)) et [déploiement de WebParts dans SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

## <a name="safe-against-script-property"></a>Propriété de script sécurisée
 L' *injection de script* est l’insertion de code potentiellement malveillant dans des contrôles ou des pages Web. Pour aider à protéger les sites SharePoint 2010 contre l’injection de script, les contributeurs ne peuvent pas afficher ou modifier des composants WebPart ou leurs propriétés par défaut. Ce comportement est contrôlé par un attribut SafeControl appelé SafeAgainstScript. Dans [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] , définissez cet attribut dans le sous-ensemble d' **entrées de contrôle sécurisé** d’un élément de projet **par rapport à un script**. Pour plus d’informations, consultez fournir des informations sur le [package et le déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) et [Comment : marquer des contrôles comme des contrôles sécurisés](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Contrôle de compte d’utilisateur Vista et Windows 7
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] et [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporer une fonctionnalité de sécurité connue sous le nom de contrôle de compte d’utilisateur (UAC). Pour développer des solutions SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sur [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] les [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] systèmes et, le contrôle de compte d’utilisateur requiert que vous exécutiez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en tant qu’administrateur système. Dans le menu **Démarrer** , ouvrez le menu contextuel de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , puis choisissez **exécuter en tant qu’administrateur**.

 Pour configurer le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] raccourci pour qu’il s’exécute toujours en tant qu’administrateur, ouvrez le menu contextuel, choisissez **Propriétés**, cliquez sur le bouton **avancé** dans la boîte de dialogue **Propriétés** , puis activez la case à cocher **exécuter en tant qu’administrateur** .

 Pour plus d’informations, consultez [comprendre et configurer le contrôle de compte d’utilisateur dans Windows Vista](/previous-versions/windows/it-pro/windows-vista/cc709628(v=ws.10)). et [le contrôle de compte d’utilisateur Windows 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731416(v=ws.10)).

## <a name="sharepoint-permissions-considerations"></a>Considérations relatives aux autorisations SharePoint
 Pour développer des solutions SharePoint, vous devez disposer des autorisations suffisantes pour exécuter et déboguer des solutions SharePoint. Avant de pouvoir tester une solution SharePoint, suivez les étapes ci-dessous pour vous assurer que vous disposez des autorisations nécessaires :

1. Ajoutez votre compte d’utilisateur en tant qu’administrateur sur le système.

2. Ajoutez votre compte d’utilisateur en tant qu’administrateur de batterie de serveurs pour le serveur SharePoint.

    1. Dans l’administration centrale de SharePoint 2010, choisissez le lien **gérer le groupe administrateurs de batterie** .

    2. Dans la page administrateurs de la **batterie de serveurs** , choisissez l’option **nouveau** menu

3. Ajoutez votre compte d’utilisateur au groupe de WSS_ADMIN_WPG.

## <a name="additional-security-resources"></a>Options de sécurité supplémentaires
 Pour plus d’informations sur les problèmes de sécurité, consultez les rubriques suivantes.

### <a name="visual-studio-security"></a>sécurité (Visual Studio)

- [Sécurité et autorisations utilisateur](/previous-versions/visualstudio/visual-studio-2010/ms165099(v=vs.100))

- [Sécurité dans le code natif et .NET Framework](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))

- [Sécurité dans le .NET Framework](/previous-versions/dotnet/netframework-4.0/fkytk30f(v=vs.100))

### <a name="sharepoint-security"></a>Sécurité SharePoint

- [Administration et sécurité de SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee537811(v=office.14))

- [Centre de ressources de sécurité SharePoint](/sharepoint/dev/)

- [Sécurisation de WebParts dans SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768613(v=office.14))

- [Amélioration de la sécurité des applications Web : menaces et contre-mesures](/previous-versions/msp-n-p/ff649874(v=pandp.10))

### <a name="general-security"></a>Sécurité générale

- [Cycle de vie de développement de sécurité MSDN](https://www.microsoft.com/msrc?rtc=1)

- [Création d’applications ASP.NET sécurisées : authentification, autorisation et communication sécurisée](/previous-versions/msp-n-p/ff649100(v=pandp.10))

## <a name="see-also"></a>Voir aussi

- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)