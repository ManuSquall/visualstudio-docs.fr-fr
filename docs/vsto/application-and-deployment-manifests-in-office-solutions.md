---
title: Manifestes d’application et de déploiement dans les solutions Office
description: Découvrez comment un manifeste d’application est un fichier XML qui fournit des informations utilisées par une solution Office pour localiser et mettre à jour ses assemblys.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 584d2414235ca70bd8a8fbcb6d2b4e2a31a1828b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965744"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Manifestes d’application et de déploiement dans les solutions Office
  Un manifeste d'application est un fichier XML qui fournit les informations utilisées par une solution Office pour localiser ses assemblys et les mettre à jour. Un manifeste d'application peut être utilisé avec un manifeste de déploiement, qui est un fichier XML stocké sur le serveur fournissant les informations nécessaires à la localisation de la version la plus récente du manifeste d'application et des assemblys.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Structure de manifeste pour les solutions Office
 Pour les solutions Microsoft Office créées à l'aide des Outils de développement Office dans Visual Studio, tous les manifestes sont basés sur le schéma ClickOnce standard. Quand vous déployez vos solutions Office, les manifestes d’application pour les projets au niveau du document et les projets de complément VSTO se trouvent dans le cache ClickOnce. Les manifestes de déploiement ne sont pas copiés sur l'ordinateur client.

 Pour plus d’informations sur le contenu des manifestes d’application et de déploiement pour les projets Office, consultez [manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md) et [manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md).

## <a name="create-application-and-deployment-manifests"></a>Créer des manifestes d’application et de déploiement
 Les manifestes d'application sont créés automatiquement dans le cadre du processus de génération. Chaque fois que vous générez un projet au niveau du document, l'emplacement du manifeste de déploiement est incorporé dans le document comme une propriété de document personnalisée. Pour les compléments VSTO, l’emplacement du manifeste de déploiement est stocké dans le Registre.

 Pour plus d’informations sur l' **Assistant Publication**, consultez [déployer une solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

 Pour plus d’informations sur la façon dont les manifestes fonctionnent avec les solutions Office, consultez [déployer une solution Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Voir aussi

- [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
- [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)