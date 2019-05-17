---
title: 'Procédure pas à pas : Téléchargement d’assemblys satellites à la demande avec l’API à l’aide du concepteur du déploiement ClickOnce | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb3003ebf8fe102caac1dabfb4c87de521a57c77
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405907"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Procédure pas à pas : Télécharger des assemblys satellites à la demande avec l’API à l’aide du concepteur du déploiement ClickOnce
Les applications Windows Forms peuvent être configurées pour plusieurs cultures à l’aide d’assemblys satellites. Un *assembly satellite* contient des ressources d’application pour une culture autre que la culture par défaut de l’application.

 Comme indiqué dans [localisation d’Applications ClickOnce](../deployment/localizing-clickonce-applications.md), vous pouvez inclure plusieurs assemblys satellites pour plusieurs cultures au sein du même [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement. Par défaut, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] télécharge tous les assemblys satellites de votre déploiement sur l’ordinateur client, même si un seul client n’a probablement besoin que d’un assembly satellite.

 Cette procédure pas à pas explique comment marquer vos assemblys satellites comme facultatifs et télécharger uniquement l’assembly dont a besoin un ordinateur client pour ses paramètres de culture actuels.

> [!NOTE]
> À des fins de test, les exemples de code suivants définissent par programmation la culture avec la valeur `ja-JP`. Consultez la section « Étapes suivantes » plus loin dans cette rubrique pour plus d’informations sur l’adaptation de ce code à un environnement de production.

### <a name="to-mark-satellite-assemblies-as-optional"></a>Pour marquer les assemblys satellites comme étant facultatifs

1. Générez votre projet. Vous obtenez des assemblys satellites pour toutes les cultures dans lesquelles vous effectuez la localisation.

2. Cliquez avec le bouton droit sur le nom de votre projet dans l’Explorateur de solutions, puis cliquez sur **Propriétés**.

3. Cliquez sur l’onglet **Publier**, puis sur **Fichiers d’application**.

4. Cochez la case **Afficher tous les fichiers** pour afficher les assemblys satellites. Par défaut, tous les assemblys satellites sont inclus dans votre déploiement et sont visibles dans cette boîte de dialogue.

     Le nom d’un assembly satellite se présente sous la forme *\<CodeISO\ApplicationName.resources.dll*, où \<CodeISO> est un identificateur de langue au format RFC 1766.

5. Cliquez sur **Nouveau** dans la liste **Groupe de téléchargement** pour chaque identificateur de langue. Quand vous êtes invité à entrer un nom de groupe de téléchargement, indiquez l'identificateur de langue. Par exemple, pour un assembly satellite japonais, spécifiez le nom de groupe de téléchargement `ja-JP`.

6. Fermez la boîte de dialogue **Fichiers d’application**.

### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>Pour télécharger des assemblys satellites à la demande en C\#

1. Ouvrez le fichier *Program.cs*. Si ce fichier ne s’affiche pas dans l’Explorateur de solutions, sélectionnez votre projet et, dans le menu **Projet**, cliquez sur **Afficher tous les fichiers**.

2. Utilisez le code suivant pour télécharger l'assembly satellite approprié et démarrer votre application.

     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]

### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Pour télécharger des assemblys satellites à la demande en Visual Basic

1. Dans la fenêtre **Propriétés** de l’application, cliquez sur l’onglet **Application**.

2. En bas de cette page, cliquez sur **Afficher les événements de l’application**.

3. Ajoutez les importations suivantes au début du fichier *ApplicationEvents.VB*.

     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]

4. Ajoutez le code suivant à la classe `MyApplication` .

     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]

## <a name="next-steps"></a>Étapes suivantes
 Dans un environnement de production, vous aurez probablement besoin de supprimer la ligne dans les exemples de code qui définit <xref:System.Threading.Thread.CurrentUICulture%2A> avec une valeur spécifique, car les ordinateurs clients ont la valeur correcte définie par défaut. Quand votre application s’exécute sur un ordinateur client japonais, par exemple, <xref:System.Threading.Thread.CurrentUICulture%2A> aura la valeur `ja-JP` par défaut. La définition par programmation est un bon moyen de tester vos assemblys satellites avant de déployer votre application.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : Télécharger des assemblys satellites à la demande avec l’API du déploiement ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)
- [Localiser des applications ClickOnce](../deployment/localizing-clickonce-applications.md)
