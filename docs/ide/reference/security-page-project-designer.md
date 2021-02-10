---
title: Page Sécurité, Concepteur de projets
description: La page Sécurité du Concepteur de projets permet de configurer les paramètres de sécurité d’accès du code pour les applications qui sont déployées avec un déploiement ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 426179eb20fcb71ac02039c3b2be20dab6f685b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957853"
---
# <a name="security-page-project-designer"></a>Page Sécurité, Concepteur de projets

La page **Sécurité** du **Concepteur de projets** permet de configurer les paramètres de sécurité d’accès du code pour les applications qui sont déployées avec un déploiement ClickOnce. Pour plus d’informations, consultez [sécurité d’accès du code pour les applications ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Pour accéder à la page **Sécurité**, cliquez sur un nœud de projet dans **l’Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Quand le **Concepteur de projets** apparaît, cliquez sur l’onglet **Sécurité**.

## <a name="security-settings"></a>Paramètres de sécurité

 **Activer les paramètres de sécurité ClickOnce**

Détermine si les paramètres de sécurité sont activés au moment du design. Quand cette option est désactivée, aucune autre option de la page **Sécurité** n’est disponible.

> [!NOTE]
> Lors de la publication d’une application à l’aide de l’Assistant **Publication**, cette option est automatiquement activée.

Quand vous sélectionnez cette option, vous avez la possibilité de sélectionner l’une des deux cases d’option suivantes : **Il s’agit d’une application de confiance totale** ou **Il s’agit d’une application de confiance partielle**.

Cette option est sélectionnée par défaut pour les projets d’application de navigateur web WPF.

Cette option est désactivée par défaut pour tous les autres types de projet.

 **Il s’agit d’une application de confiance totale**

Si vous sélectionnez cette option, l’application demande des autorisations Confiance totale quand elle est installée ou exécutée sur un ordinateur client. Évitez d’utiliser Confiance totale, car un accès illimité aux ressources, telles que le système de fichiers et le Registre, sera accordé à votre application.

Par défaut, cette option a la valeur Confiance partielle pour les projets d’application de navigateur web WPF.

Par défaut, cette option a la valeur Confiance totale pour tous les autres types de projet.

 **Il s'agit d'une application de confiance partielle**

Si vous sélectionnez cette option, l’application demande des autorisations Confiance partielle quand elle est installée ou exécutée sur un ordinateur client. *Confiance partielle* signifie que seules les actions autorisées sous les autorisations de sécurité d’accès du code demandées s’exécuteront. Pour plus d’informations sur la configuration d’autorisations de sécurité, consultez [Sécurité d’accès du code pour les applications ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Vous pouvez spécifier les paramètres de sécurité Confiance partielle en configurant les options dans la zone **Autorisations de sécurité ClickOnce**.

## <a name="clickonce-security-permissions"></a>Autorisations de sécurité ClickOnce

 **Zone à partir de laquelle votre application sera installée**

Spécifie un ensemble par défaut d’autorisations de sécurité d’accès du code. Choisissez **Internet** ou **Intranet local** pour un ensemble d’autorisations restreintes, ou **(Personnalisé)** pour configurer un ensemble d’autorisations personnalisées. Si l’application demande plus d’autorisations que celles accordées dans une zone, une invite d’approbation ClickOnce s’affiche pour l’utilisateur final afin d’accorder les autorisations supplémentaires. Pour plus d’informations sur la configuration d’autorisations de sécurité, consultez [Sécurité d’accès du code pour les applications ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Par défaut, cette option a la valeur **Internet** pour les projets d’application de navigateur web WPF.

 **Modifier les autorisations XML**

Ouvre le modèle de manifeste de l’application (app.manifest) pour configurer les autorisations pour l’ensemble d’autorisations **(Personnalisé)**.

 **Avancée**

Ouvre la [boîte de dialogue Paramètres de sécurité avancés](../../ide/reference/advanced-security-settings-dialog-box.md) qui permet de configurer les paramètres pour déboguer les applications avec des autorisations restreintes. Ces paramètres sont vérifiés pendant le débogage et les exceptions d’autorisation indiquent que votre application peut avoir besoin de plus d’autorisations que défini dans une zone.

## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [Sécurité d’accès du code pour les applications ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md)
- [Comment : activer les paramètres de sécurité ClickOnce](../../deployment/how-to-enable-clickonce-security-settings.md)
- [Guide pratique pour définir une zone de sécurité pour une application ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Comment : définir des autorisations personnalisées pour une application ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Sécuriser les applications ClickOnce](../../deployment/securing-clickonce-applications.md)
- [Sécurité et déploiement ClickOnce](../../deployment/clickonce-security-and-deployment.md)
- [Informations de référence sur les propriétés de projet](../../ide/reference/project-properties-reference.md)
- [Paramètres de sécurité avancés, boîte de dialogue](../../ide/reference/advanced-security-settings-dialog-box.md)
