---
title: Configuration requise pour développer des Solutions SharePoint | Documents Microsoft
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
- SharePoint development in Visual Studio, prerequisites
- SharePoint development in Visual Studio, requirements
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2cb92476d64abebb0dae24109e57940a19505cc1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="requirements-for-developing-sharepoint-solutions"></a>Configuration requise pour développer des solutions SharePoint
 
Vous devez installer les composants requis suivants sur le système avant de pouvoir utiliser les outils de développement de solution SharePoint inclus dans Visual Studio :

- Visual Studio avec c# ou Visual Basic ou une édition de Visual Studio Application Lifecycle Management (ALM).

- [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] installé sur 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] ou 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.

     ou

- [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] installé sur 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] ou 64 bits [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.

> [!NOTE]
> Alors que seuls les systèmes d’exploitation serveur sont officiellement pris en charge par SharePoint, deux systèmes d’exploitation de client sont autorisées : [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] et [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1. Pour plus d’informations, consultez [Guide d’Installation de SharePoint Server 2010 développeur station de travail](http://go.microsoft.com/fwlink/?LinkID=164557).

Types de projets Business Data Connectivity (BDC) modèle exigent que [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] être installés sur le système.

Pour développer des solutions SharePoint dans Visual Studio, vous devez installer SharePoint sur le même ordinateur que Visual Studio. En outre, les outils de développement SharePoint prennent uniquement en charge une configuration autonome de SharePoint ; ils ne permettent pas une configuration de batterie de serveurs (distant).

> [!NOTE]
> Les projets SharePoint dans Visual Studio prennent uniquement en charge [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]. Si vous sélectionnez [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] pour un nouveau projet SharePoint, il continuera de cibler [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].

Pour plus d’informations sur l’installation [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], consultez [installer Visual Studio](../install/install-visual-studio.md).

## <a name="vista-and-windows-7-user-account-control-uac"></a>Vista et contrôle de compte d’utilisateur (UAC) Windows 7

[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] et [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporer une fonctionnalité de sécurité qui est connue en tant que le contrôle de compte d’utilisateur (UAC). Pour développer des solutions SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sur [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] et [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] systèmes, l’UAC exige que vous exécutez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en tant qu’un administrateur système. Sur le bureau, ouvrez le menu contextuel de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], puis choisissez **exécuter en tant qu’administrateur**.

Pour configurer le raccourci du bureau soit toujours exécuté en tant qu’administrateur, ouvrez le menu contextuel, choisissez **propriétés**, choisissez le **avancé** bouton, puis sélectionnez le **exécuter en tant qu’administrateur**  case à cocher.

Pour plus d’informations, consultez [présentation et configuration des contrôle de compte utilisateur dans Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). et [contrôle de compte d’utilisateur Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).

## <a name="sharepoint-permissions-considerations"></a>Considérations relatives à des autorisations SharePoint

Pour développer des solutions SharePoint, vous devez disposer des autorisations suffisantes pour exécuter et déboguer des solutions SharePoint. Avant de pouvoir tester une solution SharePoint, procédez comme suit pour vous assurer que vous disposez des autorisations nécessaires :

1. Ajoutez votre compte d’utilisateur en tant qu’administrateur sur le système.

2. Ajoutez votre compte d’utilisateur en tant qu’un administrateur de batterie de serveurs pour le serveur SharePoint.

    1. Dans l’Administration centrale de SharePoint, choisissez le **gérer le groupe Administrateurs de batterie de serveurs** lien.

    2. Sur le **administrateurs de batterie** page, choisissez la **nouveau** bouton.

3. Ajoutez votre compte d’utilisateur pour au groupe WSS_ADMIN_WPG.

## <a name="see-also"></a>Voir aussi

[Mise en route &#40;développement SharePoint dans Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)