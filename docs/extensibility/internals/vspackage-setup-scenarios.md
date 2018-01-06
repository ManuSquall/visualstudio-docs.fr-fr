---
title: "Scénarios d’installation de VSPackage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dea9d25f211ca5042234c0400b2a10086136f49c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="vspackage-setup-scenarios"></a>Scénarios d’installation du package VS
Il est important de votre programme d’installation de VSPackage pour une flexibilité de conception. Par exemple, vous devrez peut-être libérer un correctif de sécurité dans le futur, ou vous pouvez modifier une stratégie d’entreprise qui nécessite la prise en charge le contrôle de version côte à côte approfondie.  
  
 Dans [prise en charge de plusieurs Versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), vous pouvez découvrir les avantages et les problèmes de prise en charge des installations côte à côte de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avec les installations de votre VSPackage partagées ou côte à côte. En bref, les packages VS côte à côte vous donnent le plus de flexibilité pour prendre en charge les nouvelles fonctionnalités de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Les scénarios présentés dans cette rubrique ne sont pas vos choix uniquement, mais ils sont présentés comme des pratiques recommandées.  
  
## <a name="components-privacy-and-sharing"></a>Composants de confidentialité et de partage  
  
##### <a name="make-your-components-independent"></a>Créer des composants indépendants  
 Une fois que vous identifiez et remplissez un composant, attribuer un `GUID`et le déploiement du composant, vous ne pouvez pas modifier sa composition. Si vous ne modifiez pas les composition d’un composant, le composant résultant doit être un nouveau composant avec un nouveau `GUID`. Étant donné ces faits, la plus grande flexibilité de contrôle de version est accordée en apportant de chaque unité indépendante, indépendant de composant. Pour plus d’informations sur les règles qui régissent les composants, consultez [la modification du Code du composant](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) et [que se passe-t-il si les règles de composant sont interrompues ?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Ne mélangez pas les ressources partagées et privées d’un composant  
 Décompte de références se produit au niveau du composant. Par conséquent, des ressources partagées et privées dans un composant de mélange rend impossible à mettre à jour des ressources privés, tel qu’un fichier exécutable, sans également remplacer des ressources partagées. Ce scénario crée des problèmes de compatibilité descendante et vous empêche de créer la fonctionnalité de côte-à-côte.  
  
 Par exemple, les valeurs de Registre utilisé pour inscrire votre VSPackage avec la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] doit être conservée dans un composant distinct de celui utilisé pour inscrire votre VSPackage avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Valeurs de Registre ou des fichiers partagés vont encore un autre composant.  
  
## <a name="scenario-1-shared-vspackage"></a>Scénario 1 : VSPackage partagé  
 Dans ce scénario, un VSPackage partagé (un seul fichier binaire qui prend en charge plusieurs versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) est fourni dans un package Windows Installer. L’enregistrement avec chaque version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est contrôlé par les fonctionnalités sélectionnables par l’utilisateur. Cela signifie également que lorsque assignés à séparer les fonctionnalités, chaque composant peut être sélectionné individuellement pour l’installation ou la désinstallation, donne le contrôle de l’intégration de VSPackage dans différentes versions de l’utilisateur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Consultez [fonctionnalités du programme d’installation Windows](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) pour plus d’informations sur l’utilisation des fonctionnalités dans les packages de programme d’installation de Windows.)  
  
 ![Graphique VSPackage partagé VS](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")  
Programme d’installation du package VS partagé  
  
 Comme indiqué dans l’illustration, les composants partagés sont apportées à la partie de la fonctionnalité Feat_Common, qui est toujours installée. En rendant les fonctionnalités Feat_VS2002 et Feat_VS2003 visibles, les utilisateurs peuvent choisir au moment de l’installation dans les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qu’ils souhaitent le VSPackage pour intégrer. Utilisateurs peuvent également utiliser le mode de maintenance de Windows Installer pour ajouter ou supprimer des fonctionnalités, qui ajoute ou supprime les informations sur le package d’inscription à partir de différentes versions de qui dans ce cas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  La colonne d’affichage d’une fonctionnalité 0 le masque. Une valeur de colonne de niveau bas, comme 1, permet de s’assurer qu’il sera toujours installé. Pour plus d’informations, consultez [INSTALLLEVEL propriété](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) et [Table des fonctionnalités](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Scénario 2 : Mise à jour VSPackage partagé  
 Dans ce scénario, une version mise à jour de l’installer dans le scénario 1 VSPackage est fournie. Dans la discussion, la mise à jour ajoute la prise en charge de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], mais elle peut également être un simple sécurité correctif ou résolution de bogue service pack. Les règles du programme d’installation Windows pour l’installation des composants les plus récents requièrent que les composants inchangées déjà présent sur le système ne sont pas recopiés. Dans ce cas, un système avec la version 1.0 déjà présent sera remplacer le composant de mise à jour Comp_MyVSPackage.dll et permettre aux utilisateurs de choisir d’ajouter la nouvelle fonctionnalité Feat_VS2005 avec son composant Comp_VS2005_Reg.  
  
> [!CAUTION]
>  Chaque fois qu’un VSPackage est partagé entre plusieurs versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], il est essentiel que les versions ultérieures du VSPackage assurer la compatibilité descendante avec les versions antérieures de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Où vous ne pouvez pas assurer la compatibilité descendante, vous devez utiliser les VSPackages côte à côte, privés. Pour plus d’informations, consultez [prise en charge de plusieurs Versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Image de mise à jour du Package VS partagé](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Partagé du programme d’installation de mise à jour de VSPackage  
  
 Ce scénario présente un nouveau programme d’installation VSPackage, tirant parti de la prise en charge de Windows Installer pour les mises à niveau mineures. Les utilisateurs installent simplement la version 1.1, et il met à niveau la version 1.0. Toutefois, il n’est pas nécessaire de disposer de la version 1.0 sur le système. Le même programme d’installation installera la version 1.1 sur un système sans version 1.0. L’avantage pour fournir des mises à niveau mineures de cette manière, il n’est pas nécessaire de passer par le travail de développement d’un programme d’installation de mise à niveau et un programme d’installation complète. Un programme d’installation effectue les deux tâches. Un correctif de sécurité ou un service pack peut à la place tirer parti des correctifs de Windows Installer. Pour plus d’informations, consultez [mises à niveau et mise à jour corrective](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Scénario 3 : Côte-à-côte VSPackage  
 Ce scénario présente deux programmes d’installation VSPackage : une pour chaque version de Visual Studio .NET 2003 et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Chaque programme d’installation installe un côte à côte ou privé, le VSPackage (qui est spécifiquement construit et installé une version particulière de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]). Chaque package Visual Studio est dans son propre composant. Par conséquent, chacun pouvant être traitée individuellement avec les correctifs ou de gestion des mises à jour. La DLL VSPackage est désormais spécifique à la version, il est donc plus sûr inclure les informations d’enregistrement dans le même composant en tant que la DLL.  
  
 ![VS côte &#45; par &#45; Graphique du Package VS côte](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")  
Programme d’installation du package VS côte à côte  
  
 Chaque programme d’installation inclut également le code qui est partagé entre les deux programmes d’installation. Si le code partagé est installé dans un emplacement commun, installez les deux fichiers .msi installe le code partagé qu’une seule fois. Le programme d’installation deuxième incrémente un décompte de références sur le composant. Le nombre de références garantit que, si un des VSPackages est désinstallé, le code partagé restent pour le package Visual Studio. Si le deuxième VSPackage est désinstallé ainsi, le code partagé sera supprimé.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Scénario 4 : Mise à jour du package VS côte à côte  
 Dans ce scénario, votre VSPackage pour [!INCLUDE[vsprvslong](../../code-quality/includes/vsprvslong_md.md)] subi à partir d’une sécurité vulnérabilité et vous devez émettre une mise à jour. Comme dans le scénario 2, vous pouvez créer un nouveau fichier .msi qui met à jour une installation existante afin d’inclure le correctif de sécurité, ainsi que de déployer de nouvelles installations avec le correctif de sécurité déjà en place.  
  
 Dans ce cas, le VSPackage est un VSPackage managé installé dans le global assembly cache (GAC). Quand vous le régénérez pour inclure le correctif de sécurité, vous devez modifier la partie de numéro de révision du numéro de version d’assembly. Les informations d’inscription pour le nouveau numéro de version d’assembly remplace la version précédente, à l’origine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour charger l’assembly fixe.  
  
 ![VS côte &#45; par &#45; Graphique de mise à jour du Package VS côte](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")  
Programme d’installation de mise à jour de VSPackage côte à côte  
  
 **Remarque** pour plus d’informations sur le déploiement d’assemblys côte à côte, consultez [ce qui simplifie le déploiement et la résolution des DLL Hell avec le .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Programme d’installation de Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Prise en charge de plusieurs versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)