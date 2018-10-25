---
title: Sécurité d’accès du code pour les Applications ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.XBAPProjectPropertiesSecurity.HowTo
- vb.XBAProjectPropertiesSecurity.HowTo
- vb.ProjectPropertiesSecurity.HowTo
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], security
- ClickOnce applications, caspol
- security [ClickOnce], WPF browser-hosted applications
- security [ClickOnce], ClickOnce applications
- ClickOnce applications, code access security policies
- security, ClickOnce
ms.assetid: 04b104d0-0bd3-4ccb-b164-1de92d234487
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ea1f91a50180dce6edec17afead5649ecd3e1f50
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816064"
---
# <a name="code-access-security-for-clickonce-applications"></a>Sécurité d'accès du code pour les applications ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les applications ClickOnce sont basées sur le .NET Framework et sont soumises à des contraintes de sécurité d’accès du code. Pour cette raison, il est important de comprendre les implications de la sécurité d’accès du code et d’écrire vos applications ClickOnce en conséquence.  
  
 La sécurité d'accès du code est un mécanisme dans .NET Framework qui permet de limiter l'accès du code aux ressources et aux opérations protégées. Vous devez configurer les autorisations de sécurité d'accès du code pour votre application ClickOnce afin d'utiliser la zone appropriée pour l'emplacement du programme d'installation de l'application. Dans la plupart des cas, vous pouvez choisir la zone **Internet** pour un jeu d'autorisations limité ou la zone **Intranet local** pour un jeu d'autorisations plus complet.  
  
## <a name="default-clickonce-code-access-security"></a>Sécurité d'accès du code ClickOnce par défaut  
 Par défaut, une application ClickOnce reçoit des autorisations Confiance totale quand elle est installée ou exécutée sur un ordinateur client.  
  
- Une application ayant des autorisations Confiance totale dispose d'un accès illimité aux ressources, telles que le système de fichiers et le Registre. Cela signifie que votre application, ainsi que le système de l'utilisateur final, peuvent être potentiellement exploités par du code malveillant.  
  
- Quand une application nécessite des autorisations Confiance totale, l'utilisateur final peut être invité à accorder des autorisations à l'application. Cela signifie que l'application n'est pas réellement une application ClickOnce et que l'invite peut porter à confusion pour les utilisateurs moins expérimentés.  
  
  > [!NOTE]
  >  Lors de l'installation d'une application à partir d'un média amovible, tel qu'un CD-ROM, l'utilisateur ne reçoit pas d'invite. En outre, un administrateur réseau peut configurer la stratégie réseau pour que les utilisateurs ne reçoivent pas d'invite quand ils installent une application provenant d'une source approuvée. Pour plus d'informations, consultez [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
  Pour restreindre les autorisations accordées à une application ClickOnce, vous pouvez modifier les autorisations de sécurité d'accès du code de votre application afin de demander la zone la plus appropriée aux autorisations que votre application nécessite. Dans la plupart des cas, vous pouvez choisir la zone à partir de laquelle l'application est déployée. Par exemple, si votre application est une application d'entreprise, utilisez la zone **Intranet local** . S'il s'agit d'une application Internet, utilisez la zone **Internet** .  
  
## <a name="configuring-security-permissions"></a>Configuration des autorisations de sécurité  
 Vous devez toujours configurer votre application ClickOnce pour demander la zone permettant de limiter les autorisations de sécurité d'accès du code. Vous pouvez définir les autorisations de sécurité dans la page **Sécurité** du **Concepteur de projets**.  
  
 La page **Sécurité** du **Concepteur de projets** contient une case à cocher **Activer les paramètres de sécurité ClickOnce** . Quand cette case est cochée, les demandes d'autorisation de sécurité sont ajoutées au manifeste de déploiement de votre application. Au moment de l'installation, l'utilisateur est invité à accorder des autorisations si les autorisations demandées dépassent les autorisations par défaut de la zone à partir de laquelle l'application est déployée. Pour plus d'informations, consultez [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md).  
  
 Différents niveaux d'autorisations sont accordés, sans demande de confirmation, à des applications déployées à partir d'emplacements différents. Par exemple, quand une application est déployée à partir d'Internet, elle reçoit un jeu d'autorisations très restrictif. Si elle est installée à partir d'un intranet local, elle reçoit des autorisations plus larges. Si elle est installée à partir d'un CD-ROM, elle reçoit des autorisations Confiance totale.  
  
 Pour définir des autorisations, commencez par choisir une zone de sécurité dans la liste **Zone** de la page **Sécurité** . Si vous comptez déployer votre application à partir de plusieurs zones, choisissez la zone avec le moins d'autorisations. Pour plus d'informations, consultez [Comment : définir une zone de sécurité pour une application ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).  
  
 Les propriétés qui peuvent être définies varient selon le jeu d'autorisations, mais tous les jeux d'autorisations ne possèdent pas des propriétés configurables. Pour plus d'informations sur la liste complète des autorisations que votre application peut demander, consultez <xref:System.Security.Permissions>. Pour plus d’informations sur la façon de définir des autorisations pour une zone personnalisée, consultez [Comment : définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
## <a name="debugging-an-application-that-has-restricted-permissions"></a>Débogage d'une application disposant d'autorisations restreintes  
 En tant que développeur, vous utilisez très probablement votre ordinateur de développement avec les autorisations Confiance totale. Par conséquent, vous ne voyez pas apparaître les mêmes exceptions de sécurité lors du débogage de l'application que celles pouvant être rencontrées par les utilisateurs qui exécutent l'application avec des autorisations restreintes.  
  
 Pour intercepter ces exceptions, vous devez déboguer l'application avec les mêmes autorisations que l'utilisateur final. Le débogage avec des autorisations restreintes peut être activé dans la page **Sécurité** du **Concepteur de projets**.  
  
 Quand vous déboguez une application avec des autorisations restreintes, des exceptions sont levées pour toutes les demandes de sécurité de code qui n'ont pas été activées dans la page **Sécurité** . Un programme d'assistance de l'exception affiche alors des suggestions de modification de votre code pour empêcher l'exception.  
  
 De plus, lors de l’écriture du code, la fonctionnalité IntelliSense de l’éditeur de code désactive tous les membres qui ne sont pas inclus dans les autorisations de sécurité que vous avez configurées.  
  
 Pour plus d'informations, consultez [Comment : déboguer une application ClickOnce avec des autorisations restreintes](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
## <a name="security-permissions-for-browser-hosted-applications"></a>Autorisations de sécurité pour les applications hébergées dans un navigateur  
 Visual Studio fournit les types de projets suivants pour les applications Windows Presentation Foundation (WPF) :  
  
- Application de fenêtres WPF  
  
- Application de navigateur web WPF  
  
- Bibliothèque de contrôles personnalisés WPF  
  
- Bibliothèque de services WPF  
  
  Parmi ces types de projets, seules les applications de navigateur web WPF sont hébergées dans un navigateur web, et nécessitent donc des paramètres de déploiement et de sécurité particuliers. Les paramètres de sécurité par défaut de ces applications sont les suivants :  
  
- **Activer les paramètres de sécurité ClickOnce**  
  
- **Il s'agit d'une application de confiance partielle**  
  
- **Zone Internet** (avec le jeu d'autorisations par défaut pour les applications de navigateur web WPF sélectionnées)  
  
  Dans la boîte de dialogue **Paramètres de sécurité avancés** , la case à cocher **Déboguer cette application à l'aide du jeu d'autorisations sélectionné** est cochée et désactivée. En effet, le débogage par zone ne peut pas être désactivé pour les applications hébergées dans un navigateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Guide pratique pour activer les paramètres de sécurité ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Guide pratique pour définir une zone de sécurité pour une application ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Guide pratique pour définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [How to: Debug a ClickOnce Application with Restricted Permissions](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md)   
 [Page Sécurité, Concepteur de projet](../ide/reference/security-page-project-designer.md)



