---
title: Comparaison des solutions VBA et Office dans Visual Studio
description: Découvrez les différences entre les solutions Microsoft Visual Basic pour Applications (VBA) et Microsoft Office dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d07975061a7b2f5f655bf7f4339671f28fe14c9
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526416"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Comparaison des solutions VBA et Office dans Visual Studio
  Microsoft Visual Basic pour Applications (VBA) utilise du code non managé étroitement intégré aux applications Office. Les projets Microsoft Office créés à l'aide de Visual Studio vous permettent de tirer parti des outils de conception de .NET Framework et Visual Studio.

 Pour plus d’informations sur les types de solutions Office que vous pouvez créer à l’aide de Visual Studio, consultez [vue d’ensemble du développement des solutions office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="comparison"></a>Comparaison
 Le tableau suivant répertorie les principales différences entre les solutions VBA et les solutions Office dans Visual Studio.

|Solutions VBA|Solutions Office dans Visual Studio|
|-------------------|---------------------------------------|
|Utilisent du code qui est lié à un document spécifique et qui est stocké de façon persistante avec ce document.|Utilise du code qui est stocké séparément du document (pour les personnalisations au niveau du document), ou dans un assembly chargé par l’application (pour les compléments VSTO).|
|Fonctionnent avec les modèles objet Office et les API VBA.|Fournissent l'accès à la fois aux modèles objet Office et aux API [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|
|Permettent d'enregistrer des macros et simplifient le travail du développeur.|Améliorent la sécurité, facilitent la maintenance du code et permettent l'utilisation de l'environnement de développement intégré (IDE) de Visual Studio dans son intégralité.|
|Fonctionne bien pour les solutions qui tirent parti d’une intégration étroite avec les applications Office.|Conviennent pour les solutions qui utilisent les ressources complètes de Visual Studio et de [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|
|Présentent des limites d'utilisation dans l'entreprise, notamment dans les domaines de la sécurité et du déploiement.|Sont adaptées pour une utilisation dans l'entreprise.|

 Certains résultats restent plus simples et plus rapides à obtenir avec VBA. En particulier, vous pouvez continuer à utiliser VBA pour :

- les fonctions de feuille de calcul personnalisées ;

- l'enregistrement de macros.

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Combiner des solutions VBA et des solutions Office créées à l’aide de Visual Studio
 Vous pouvez appeler du code VBA à partir de solutions Office créées à l'aide de Visual Studio et, inversement, appeler du code des solutions Office créées avec Visual Studio à partir de VBA. La technique appropriée diffère selon que votre solution Office est un complément VSTO ou une personnalisation au niveau du document. Pour plus d’informations, consultez [appel de code dans des compléments VSTO à partir d’autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) et [combinaison de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Appeler du code dans des compléments VSTO à partir d’autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Combiner VBA et les personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md)
- [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)
- [Prise en main &#40;le développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
