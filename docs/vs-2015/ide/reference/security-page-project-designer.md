---
title: Page Sécurité, Concepteur de projets | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 768b0d43d8e6b52781e3f2dc2029e0b96b3a6548
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665539"
---
# <a name="security-page-project-designer"></a>Page Sécurité, Concepteur de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La page **Sécurité** du **Concepteur de projets** permet de configurer les paramètres de sécurité d’accès du code pour les applications qui sont déployées à l’aide d’un déploiement [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]. Pour plus d’informations, consultez [Sécurité d’accès du code pour les applications ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Pour accéder à la page **Sécurité**, cliquez sur un nœud de projet dans **l’Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Quand le **Concepteur de projets** apparaît, cliquez sur l’onglet **Sécurité**.

## <a name="security-settings"></a>Paramètres de sécurité
 **Activer les paramètres de sécurité ClickOnce** Détermine si les paramètres de sécurité sont activés au moment du Design. Quand cette option est désactivée, aucune autre option de la page **Sécurité** n’est disponible.

> [!NOTE]
> Lors de la publication d’une application à l’aide de l’Assistant **Publication**, cette option est automatiquement activée.

 Quand vous sélectionnez cette option, vous avez la possibilité de sélectionner l’une des deux cases d’option suivantes : **Il s’agit d’une application de confiance totale** ou **Il s’agit d’une application de confiance partielle**.

 Cette option est sélectionnée par défaut pour les projets d’application de navigateur web WPF.

 Cette option est désactivée par défaut pour tous les autres types de projet.

 **Il s’agit d’une application de confiance totale** Si vous sélectionnez cette option, l’application demande des autorisations confiance totale quand elle est installée ou exécutée sur un ordinateur client. Évitez d’utiliser Confiance totale, car un accès illimité aux ressources, telles que le système de fichiers et le Registre, sera accordé à votre application.

 Par défaut, cette option a la valeur Confiance partielle pour les projets d’application de navigateur web WPF.

 Par défaut, cette option a la valeur Confiance totale pour tous les autres types de projet.

 **Il s’agit d’une application de confiance partielle** Si vous sélectionnez cette option, l’application demande des autorisations de confiance partielle lorsqu’elle est installée ou exécutée sur un ordinateur client. *Confiance partielle* signifie que seules les actions autorisées sous les autorisations de sécurité d’accès du code demandées s’exécuteront. Pour plus d’informations sur la configuration d’autorisations de sécurité, consultez [Sécurité d’accès du code pour les applications ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Vous pouvez spécifier les paramètres de sécurité Confiance partielle en configurant les options dans la zone **Autorisations de sécurité ClickOnce**.

## <a name="clickonce-security-permissions"></a>Autorisations de sécurité ClickOnce
 **Zone à partir de laquelle votre application sera installée** Spécifie un ensemble par défaut d’autorisations de sécurité d’accès du code. Choisissez **Internet** ou **Intranet local** pour un ensemble d’autorisations restreintes, ou **(Personnalisé)** pour configurer un ensemble d’autorisations personnalisées. Si l’application demande plus d’autorisations que celles accordées dans une zone, une invite d’approbation ClickOnce s’affiche pour l’utilisateur final afin d’accorder les autorisations supplémentaires. Pour plus d’informations sur la configuration d’autorisations de sécurité, consultez [Sécurité d’accès du code pour les applications ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Par défaut, cette option a la valeur **Internet** pour les projets d’application de navigateur web WPF.

 **Modifier les autorisations XML** Ouvre le modèle de manifeste de l’application (App. manifest) pour configurer les autorisations pour le jeu d’autorisations **(personnalisé)** .

 **Paramètres avancés** Ouvre la [boîte de dialogue Paramètres de sécurité avancés](../../ide/reference/advanced-security-settings-dialog-box.md), qui permet de configurer les paramètres de débogage de l’application avec des autorisations restreintes. Ces paramètres sont vérifiés pendant le débogage et les exceptions d’autorisation indiquent que votre application peut avoir besoin de plus d’autorisations que défini dans une zone.

## <a name="see-also"></a>Voir aussi
 <xref:System.Security.Permissions.WebBrowserPermission> <xref:System.Security.Permissions.MediaPermission>
 [Sécurité d’accès du code pour les applications ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md) [Comment : activer les paramètres de sécurité ClickOnce](../../deployment/how-to-enable-clickonce-security-settings.md) [Comment : définir une zone de sécurité pour une application ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md) [Comment : définir des autorisations personnalisées pour une application ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md) [Comment : Déboguer une application ClickOnce avec des autorisations restreintes](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md) propriétés du projet de [déploiement et de sécurité ClickOnce](../../deployment/clickonce-security-and-deployment.md) [Référence](../../ide/reference/project-properties-reference.md) des [paramètres de sécurité avancés, boîte de dialogue](../../ide/reference/advanced-security-settings-dialog-box.md)
