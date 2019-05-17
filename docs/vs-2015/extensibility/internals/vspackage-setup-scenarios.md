---
title: Scénarios d’installation de VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a09b794a6cd81966df45a1b30182040d7ab9335e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696755"
---
# <a name="vspackage-setup-scenarios"></a>Scénarios d’installation de VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il est important de votre programme d’installation de package Visual Studio pour une flexibilité de conception. Par exemple, vous devrez peut-être libérer un correctif de sécurité à l’avenir, ou vous pouvez modifier une stratégie qui nécessite la prise en charge approfondie versioning côte à côte.  
  
 Dans [prenant en charge plusieurs Versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), vous pouvez découvrir les avantages et les problèmes de prise en charge des installations côte à côte de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] avec des installations partagées ou côte à côte de votre VSPackage. En bref, les packages VS côte à côte vous donnent plus de flexibilité pour prendre en charge les nouvelles fonctionnalités de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Les scénarios présentés dans cette rubrique ne sont pas vos seuls choix, mais elles sont présentées comme des pratiques recommandées.  
  
## <a name="components-privacy-and-sharing"></a>Composants, la confidentialité et le partage  
  
##### <a name="make-your-components-independent"></a>Créer des composants indépendants  
 Une fois que vous identifiez et remplissez un composant, affecter un `GUID`et le déploiement du composant, vous ne pouvez pas modifier sa composition. Si vous ne modifiez pas les composition d’un composant, le composant qui en résulte doit être un nouveau composant avec un nouveau `GUID`. Étant donné ces faits, la plus grande flexibilité de contrôle de version est offerte en rendant chaque unité indépendante, indépendant de composant. Pour plus d’informations sur les règles régissant les composants, consultez [la modification du Code de composant](https://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) et [que se passe-t-il si les règles de composant sont répartis ?](https://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Ne mélangez pas les ressources partagées et privées dans un composant  
 Comptage de références se produit au niveau du composant. Par conséquent, la combinaison de ressources partagées et privées dans un composant rend impossible à mettre à jour des ressources privées, tel qu’un fichier exécutable, sans remplacer également les ressources partagées. Ce scénario crée des problèmes de compatibilité descendante et vous empêche de créer la fonctionnalité de côte à côte.  
  
 Par exemple, les valeurs de Registre utilisé pour inscrire votre VSPackage avec le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] doivent être conservés dans un composant distinct de celui qui est utilisé pour inscrire votre VSPackage avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Valeurs de Registre ou des fichiers partagés vont dans un autre composant.  
  
## <a name="scenario-1-shared-vspackage"></a>Scénario 1 : VSPackage partagé  
 Dans ce scénario, un VSPackage partagé (un seul binaire qui prend en charge plusieurs versions de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]) est livré dans un package Windows Installer. L’inscription avec chaque version de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est contrôlé par les fonctionnalités sélectionnables par l’utilisateur. Cela signifie également que quand attribué pour séparer les fonctionnalités, chaque composant peut être sélectionné individuellement pour l’installation ou la désinstallation, donne le contrôle de l’intégration de VSPackage dans différentes versions de l’utilisateur [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. (Consultez [fonctionnalités du programme d’installation Windows](https://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) pour plus d’informations sur l’utilisation des fonctionnalités dans les packages de programme d’installation de Windows.)  
  
 ![Graphique VSPackage partagé VS](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
Programme d’installation de VSPackage partagé  
  
 Comme indiqué dans l’illustration, les composants partagés sont apportées à la partie de la fonctionnalité Feat_Common, qui est toujours installée. En rendant les fonctionnalités Feat_VS2002 et Feat_VS2003 visible, les utilisateurs peuvent choisir au moment de l’installation dans les versions de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] qu’ils souhaitent le VSPackage à intégrer. Utilisateurs peuvent également utiliser le mode de maintenance de Windows Installer pour ajouter ou supprimer des fonctionnalités, qui dans ce cas d’ajoute ou supprime les informations d’inscription de VSPackage de différentes versions de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
> [!NOTE]
> Définition de colonne d’affichage d’une fonctionnalité à 0 le masque. Une valeur de colonne de niveau faible, par exemple, 1, permet de s’assurer qu’il sera toujours installé. Pour plus d’informations, consultez [INSTALLLEVEL propriété](https://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) et [fonctionnalité Table](https://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Scénario 2 : Mise à jour de VSPackage partagé  
 Dans ce scénario, une version mise à jour de l’installeur de package Visual Studio dans le scénario 1 est expédiée. Dans la discussion, la mise à jour ajoute la prise en charge de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], mais cela peut également être un simple sécurité correctif ou correctif de bogue service pack. Les règles du programme d’installation Windows pour l’installation des composants les plus récents nécessitent que les composants inchangés déjà sur le système ne sont pas recopiés. Dans ce cas, un système avec la version 1.0 déjà présent remplace le composant mis à jour Comp_MyVSPackage.dll et permettre aux utilisateurs de choisir d’ajouter la nouvelle fonctionnalité Feat_VS2005 avec son composant Comp_VS2005_Reg.  
  
> [!CAUTION]
> Chaque fois qu’un VSPackage est partagé entre plusieurs versions de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], il est essentiel que les versions ultérieures du VSPackage assurer la compatibilité descendante avec les versions antérieures de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Où vous ne pouvez pas assurer la compatibilité descendante, vous devez utiliser les VSPackages côte à côte, privées. Pour plus d’informations, consultez [prenant en charge plusieurs Versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Image de mise à jour de Package VS partagé](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Partagé le programme d’installation de mise à jour de package Visual Studio  
  
 Ce scénario présente un nouveau programme d’installation VSPackage, en tirant parti de la prise en charge du programme d’installation Windows pour les mises à niveau mineures. Les utilisateurs installent simplement la version 1.1, et il met à niveau la version 1.0. Toutefois, il n’est pas nécessaire de disposer de la version 1.0 sur le système. Le même programme d’installation installera la version 1.1 sur un système sans version 1.0. L’avantage de fournir des mises à niveau mineures de cette manière est qu’il n’est pas nécessaire de passer par le travail de développement d’un programme d’installation de mise à niveau et un programme d’installation complète. Un programme d’installation effectue les deux tâches. Un correctif de sécurité ou un service pack peut à la place tirer parti des correctifs du programme d’installation de Windows. Pour plus d’informations, consultez [mises à niveau et mise à jour corrective](https://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Scénario 3 : Package VS côte à côte  
 Ce scénario présente deux programmes d’installation de package Visual Studio : une pour chaque version de Visual Studio .NET 2003 et [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Chaque programme d’installation installe un côte à côte, ou privé, VSPackage (celui qui est spécifiquement créé et installé une version particulière de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]). Chaque VSPackage est dans son propre composant. Par conséquent, chacune pouvant être traitée individuellement avec les correctifs logiciels ou de maintenance libère. La DLL VSPackage étant désormais spécifique à la version, il est en toute sécurité à ses informations d’inscription dans le même composant que la DLL.  
  
 ![VS côté&#45;par&#45;graphique du Package VS de côté](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Programme d’installation du package VS côte à côte  
  
 Chaque programme d’installation inclut également le code qui est partagé entre les deux programmes d’installation. Si le code partagé est installé dans un emplacement commun, installez les deux fichiers .msi installe le code partagé qu’une seule fois. Le programme d’installation deuxième incrémente un décompte de références sur le composant. Le décompte de références garantit que si un des VSPackages est désinstallé, le code partagé restent pour le package Visual Studio. Si le deuxième VSPackage est également désinstallé, le code partagé sera supprimé.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Scénario 4 : Mise à jour du package VS côte à côte  
 Dans ce scénario, votre VSPackage pour [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] subi à partir d’une sécurité vulnérabilité et vous devez émettre une mise à jour. Comme dans le scénario 2, vous pouvez créer un nouveau fichier .msi qui met à jour une installation existante afin d’inclure le correctif de sécurité, ainsi que de déployer de nouvelles installations avec le correctif de sécurité déjà en place.  
  
 Dans ce cas, le VSPackage est un VSPackage managé installé dans le global assembly cache (GAC). Lorsque vous reconstruisez ce qu’il inclue le correctif de sécurité, vous devez modifier la partie de numéro de révision du numéro de version d’assembly. Les informations d’inscription pour le nouveau numéro de version d’assembly remplace la version précédente, ce qui provoque [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour charger l’assembly fixe.  
  
 ![VS côté&#45;par&#45;graphique de mise à jour du Package côté VS](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Programme d’installation de mise à jour de package VS côte à côte  
  
 **Remarque** pour plus d’informations sur le déploiement d’assemblys côte à côte, consultez [ce qui simplifie le déploiement et la résolution de l’enfer des DLL avec le .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Programme d’installation de Windows](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Prise en charge de plusieurs versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
