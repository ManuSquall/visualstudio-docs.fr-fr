---
title: Télécharger l’assembly satellite à la demande à l’aide du concepteur ClickOnce
description: Découvrez comment marquer des assemblys satellites comme facultatifs à l’aide du concepteur et télécharger uniquement l’assembly dont a besoin un ordinateur client pour ses paramètres de culture actuels.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9e9166dbd3d6cd7ba4500e2390bd611a31bcee7b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216876"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Procédure pas à pas : Télécharger des assemblys satellites à la demande avec l’API de déploiement ClickOnce à l’aide du concepteur
Les applications Windows Forms peuvent être configurées pour plusieurs cultures à l’aide d’assemblys satellites. Un *assembly satellite* contient des ressources d’application pour une culture autre que la culture par défaut de l’application.

 Comme indiqué dans la [localisation d’applications ClickOnce](../deployment/localizing-clickonce-applications.md), vous pouvez inclure plusieurs assemblys satellites pour plusieurs cultures au sein du même [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement. Par défaut, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] télécharge tous les assemblys satellites de votre déploiement sur l’ordinateur client, même si un seul client n’a probablement besoin que d’un assembly satellite.

 Cette procédure pas à pas explique comment marquer vos assemblys satellites comme facultatifs et télécharger uniquement l’assembly dont a besoin un ordinateur client pour ses paramètres de culture actuels.

> [!NOTE]
> À des fins de test, les exemples de code suivants définissent par programmation la culture avec la valeur `ja-JP`. Consultez la section « Étapes suivantes » plus loin dans cette rubrique pour plus d’informations sur l’adaptation de ce code à un environnement de production.

### <a name="to-mark-satellite-assemblies-as-optional"></a>Pour marquer les assemblys satellites comme étant facultatifs

1. Générez votre projet. Vous obtenez des assemblys satellites pour toutes les cultures dans lesquelles vous effectuez la localisation.

2. Cliquez avec le bouton droit sur le nom de votre projet dans l’Explorateur de solutions, puis cliquez sur **Propriétés**.

3. Cliquez sur l’onglet **Publier**, puis sur **Fichiers d’application**.

4. Cochez la case **Afficher tous les fichiers** pour afficher les assemblys satellites. Par défaut, tous les assemblys satellites sont inclus dans votre déploiement et sont visibles dans cette boîte de dialogue.

     Un assembly satellite aura un nom sous la forme *\<isoCode>\ApplicationName.resources.dll*, où \<isoCode> est un identificateur de langue au format RFC 1766.

5. Cliquez sur **Nouveau** dans la liste **Groupe de téléchargement** pour chaque identificateur de langue. Quand vous êtes invité à entrer un nom de groupe de téléchargement, indiquez l'identificateur de langue. Par exemple, pour un assembly satellite japonais, vous devez spécifier le nom du groupe de téléchargement `ja-JP` .

6. Fermez la boîte de dialogue **Fichiers d’application**.

### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>Pour télécharger des assemblys satellites à la demande en C\#

1. Ouvrez le fichier *Program. cs* . Si ce fichier ne s’affiche pas dans l’Explorateur de solutions, sélectionnez votre projet et, dans le menu **Projet**, cliquez sur **Afficher tous les fichiers**.

2. Utilisez le code suivant pour télécharger l'assembly satellite approprié et démarrer votre application.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssemblies/CS/Program.cs" id="Snippet1":::

### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Pour télécharger des assemblys satellites à la demande en Visual Basic

1. Dans la fenêtre **Propriétés** de l’application, cliquez sur l’onglet **Application**.

2. En bas de cette page, cliquez sur **Afficher les événements de l’application**.

3. Ajoutez les importations suivantes au début du fichier *ApplicationEvents. vb* .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb" id="Snippet1":::

4. Ajoutez le code suivant à la classe `MyApplication` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb" id="Snippet2":::

## <a name="next-steps"></a>Étapes suivantes
 Dans un environnement de production, vous aurez probablement besoin de supprimer la ligne dans les exemples de code qui définit <xref:System.Threading.Thread.CurrentUICulture%2A> avec une valeur spécifique, car les ordinateurs clients ont la valeur correcte définie par défaut. Quand votre application s’exécute sur un ordinateur client japonais, par exemple, <xref:System.Threading.Thread.CurrentUICulture%2A> aura la valeur `ja-JP` par défaut. La définition par programmation est un bon moyen de tester vos assemblys satellites avant de déployer votre application.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : Télécharger des assemblys satellites à la demande avec l’API de déploiement ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)
- [Localiser des applications ClickOnce](../deployment/localizing-clickonce-applications.md)
