---
title: Valider votre système pendant le développement | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 33d5de340455e5e0f6a39dd9ce470d2e96327216
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262182"
---
# <a name="validate-your-system-during-development"></a>Validation de votre système pendant le développement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio peut vous aider à garder votre logiciel en cohérence avec les besoins des utilisateurs et avec l’architecture de votre système.  
  
 Pour connaître les versions de Visual Studio qui prennent en charge chacune de ces fonctionnalités, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="key-tasks"></a>Tâches clés  
 Utilisez les tâches suivantes pour valider votre logiciel.  
  
|**Tâches**|**Rubriques associées**|  
|---------------|---------------------------|  
|**Assurez-vous que votre modèle est cohérent :**<br /><br /> Selon la façon dont votre projet utilise et interprète les modèles, il peut être utile de ne pas autoriser certaines combinaisons d’éléments. Par exemple, vous pouvez restreindre les classes UML pour qu’elles portent toujours des noms conformes à [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]. Vous pouvez définir des contraintes comme celles-ci dans des extensions [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|-   [Valider votre modèle UML](../modeling/validate-your-uml-model.md)<br />-   [Définir des contraintes de validation pour les modèles UML](../modeling/define-validation-constraints-for-uml-models.md)|  
|**Assurez-vous que votre logiciel répond aux besoins des utilisateurs**:<br /><br /> Vous pouvez utiliser les spécifications et les modèles architecturaux pour mieux organiser les tests de votre système et de ses composants. Cette pratique vous permet de vous assurer que vous testez les besoins importants des utilisateurs et des autres parties prenantes, et vous aide à mettre rapidement à jour les tests quand les besoins changent.|-   [Développer des tests à partir d’un modèle](../modeling/develop-tests-from-a-model.md)|  
|**Assurez-vous que votre logiciel reste cohérent avec la conception prévue de votre système :**<br /><br /> Les diagrammes de couche décrivent les dépendances prévues entre les composants de votre application. Pendant le développement, vous pouvez vérifier que les dépendances actuelles dans le code sont conformes à la conception prévue.|-   [Créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Valider du code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>Ressources externes  
  
|**Catégorie**|**Liens**|  
|------------------|---------------|  
|**Vidéos**|![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9 : Doug sept : compréhension du Code et conception du système avec Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9 : architecture d’une Application à l’aide d’un diagramme de couche](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo") [série MSDN Comment faire : comment valider du Code à l’aide de diagrammes de couche](http://go.microsoft.com/fwlink/?LinkID=214405)|  
|**Forums**|-   [Outils de visualisation et de modélisation Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling (outils DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogs**|-   [Blog Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Articles et journaux techniques**|[Centre d’architecture MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Voir aussi  
 [Test de l'application](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [Étendre des diagrammes et des modèles UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md)   
 [Analyse et modélisation de l’architecture](../modeling/analyze-and-model-your-architecture.md)



