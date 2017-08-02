---
title: "Sc&#233;narios d’installation du package VS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, considérations relatives au déploiement"
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Sc&#233;narios d’installation du package VS
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il est important de concevoir votre programme d’installation du package VS de flexibilité. Par exemple, vous devrez peut\-être publier un correctif de sécurité à l’avenir, ou vous pouvez modifier une stratégie d’entreprise qui nécessite la prise en charge approfondie versioning côte à côte.  
  
 Dans [Prise en charge de plusieurs Versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), vous pouvez découvrir les avantages et les problèmes de prise en charge des installations côte à côte de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avec les installations de votre package VS partagées ou côte à côte. En bref, les packages VS côte à côte vous donnent le plus de flexibilité pour prendre en charge les nouvelles fonctionnalités de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Les scénarios présentés dans cette rubrique ne sont pas vos seuls choix, mais ils sont présentés comme des pratiques recommandées.  
  
## Composants, la confidentialité et partage  
  
##### Créer des composants indépendants  
 Après avoir identifié et remplir un composant, affecter une `GUID`, et le déploiement du composant, vous ne pouvez pas modifier sa composition. Si vous modifiez la composition d’un composant, le composant qui en résulte doit être un nouveau composant avec un nouveau `GUID`. Compte tenu de ces faits, la plus grande flexibilité de contrôle de version est permise en rendant chaque unité indépendante, autonome de composant. Pour plus d’informations sur les règles régissant les composants, consultez [la modification du Code de composant](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) et [que se passe\-t\-il si les règles de composant sont interrompues ?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### Ne pas mélanger les ressources partagées et privées d’un composant  
 Décompte de références se produit au niveau du composant. Par conséquent, des ressources partagées et privées dans un composant de mélange rend impossible mettre à jour des ressources privées, par exemple un fichier exécutable, sans également remplacer des ressources partagées. Ce scénario crée des problèmes de compatibilité descendante et vous empêche de créer la fonctionnalité de côte\-à\-côte.  
  
 Par exemple, les valeurs de Registre utilisé pour inscrire votre package VS avec les [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] doivent être conservés dans un composant distinct de celui utilisé pour inscrire votre package VS avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Fichiers partagés ou des valeurs de Registre aller dans un autre composant.  
  
## Scénario 1 : VSPackage partagé  
 Dans ce scénario, un VSPackage partagé \(un seul binaire qui prend en charge plusieurs versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\) est inclus dans un package Windows Installer. L’enregistrement avec chaque version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est contrôlé par les fonctionnalités sélectionnables par l’utilisateur. Cela signifie également que lorsque affecté pour séparer les fonctionnalités, chaque composant peut être individuellement sélectionné pour l’installation ou la désinstallation, plaçant l’utilisateur dans le contrôle d’intégration le VSPackage dans différentes versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. \(Voir [fonctionnalités de Windows Installer](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) pour plus d’informations sur l’utilisation de fonctions dans les packages de programme d’installation de Windows.\)  
  
 ![Graphique VSPackage partagé VS](~/docs/extensibility/internals/media/vs_sharedpackage.gif "VS\_SharedPackage")  
Programme d’installation du package VS partagé  
  
 Comme indiqué dans l’illustration, les composants partagés sont effectuées de la fonctionnalité Feat\_Common, qui est toujours installée. En apportant les fonctionnalités Feat\_VS2002 et Feat\_VS2003 visible, les utilisateurs peuvent choisir au moment de l’installation dans les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qu’ils souhaitent le VSPackage à intégrer. Utilisateurs peuvent également utiliser le mode de maintenance de Windows Installer pour ajouter ou supprimer des fonctionnalités, qui dans ce cas d’ajoute ou supprime les informations d’inscription VSPackage de différentes versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  Définition de colonne d’affichage d’une fonctionnalité 0 masque. Une valeur de colonne de niveau faible, comme 1, permet de s’assurer qu’il sera toujours installé. Pour plus d’informations, consultez [INSTALLLEVEL propriété](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) et [Table Feature](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## Scénario 2 : Mise à jour VSPackage partagé  
 Dans ce scénario, une version mise à jour de l’installeur de package VS dans le scénario 1 est fournie. Dans la discussion, la mise à jour ajoute la prise en charge de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], mais elle peut également être un simple correctif ou correctif de bogue service pack de sécurité. Règles de Windows Installer pour installer les composants les plus récents requièrent que les composants inchangés déjà sur le système sont recopiés pas. Dans ce cas, un système avec la version 1.0 déjà présent remplace le composant mis à jour Comp\_MyVSPackage.dll et permettre aux utilisateurs de choisir d’ajouter la nouvelle fonctionnalité Feat\_VS2005 avec son composant Comp\_VS2005\_Reg.  
  
> [!CAUTION]
>  Chaque fois qu’un VSPackage est partagé entre plusieurs versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], il est essentiel que les versions ultérieures du VSPackage maintenir la compatibilité descendante avec les versions antérieures de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Si vous ne pouvez pas conserver la compatibilité descendante, vous devez utiliser VSPackages côte\-à\-côte, privés. Pour plus d'informations, consultez [Prise en charge de plusieurs Versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Image de mise à jour du package VS partagé VS](~/docs/extensibility/internals/media/vs_sharedpackageupdate.gif "VS\_SharedPackageUpdate")  
Partagé du programme d’installation de la mise à jour VSPackage  
  
 Ce scénario présente un nouveau programme d’installation VSPackage, tirant parti de la prise en charge de Windows Installer pour les mises à niveau mineures. Les utilisateurs installent simplement la version 1.1, et il met à niveau la version 1.0. Toutefois, il n’est pas nécessaire de disposer de la version 1.0 sur le système. Le même programme d’installation va installer la version 1.1 sur un ordinateur sans version 1.0. L’avantage de fournir des mises à niveau mineures de cette manière, qu’il n’est pas nécessaire suivre le travail de développement d’un programme d’installation de mise à niveau et un programme d’installation complète. Un programme d’installation effectue les deux tâches. Un correctif de sécurité ou un service pack peut à la place tirer parti des correctifs de Windows Installer. Pour plus d’informations, consultez [mises à niveau et mise à jour corrective](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## Scénario 3 : Côte\-à\-côte VSPackage  
 Ce scénario présente deux programmes d’installation du package VS : une pour chaque version de Visual Studio .NET 2003 et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Chaque programme d’installation installe un côté à côte ou private, VSPackage \(celui qui est spécifiquement créé et installé une version particulière de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\). Chaque VSPackage est dans son propre composant. Par conséquent, chaque peut être traitée individuellement avec les correctifs logiciels ou de gestion des mises à jour. La DLL VSPackage étant désormais spécifique à la version, il est en toute sécurité à ses informations d’inscription dans le même composant que la DLL.  
  
 ![Graphique du package VS côte à côte VS](~/docs/extensibility/internals/media/vs_sbys_package.gif "VS\_SbyS\_Package")  
Programme d’installation du package VS côte à côte  
  
 Chaque programme d’installation inclut également le code qui est partagée entre les deux programmes d’installation. Si le code partagé est installé dans un emplacement commun, l’installation de deux fichiers .msi installe le code partagé une seule fois. Le programme d’installation deuxième incrémente un décompte de références sur le composant. Le décompte de références garantit que si un des VSPackages est désinstallé, le code partagé restent pour l’autres VSPackage. Si le deuxième VSPackage est désinstallé, le code partagé est supprimé.  
  
## Scénario 4 : Mise à jour du package VS côte à côte  
 Dans ce scénario, votre VSPackage pour [!INCLUDE[vsprvslong](../../code-quality/includes/vsprvslong_md.md)] a subi une sécurité vulnérabilité et vous devez émettre une mise à jour. Comme dans le scénario 2, vous pouvez créer un nouveau fichier .msi qui met à jour une installation existante pour inclure le correctif de sécurité, ainsi que déployer de nouvelles installations avec le correctif de sécurité déjà en place.  
  
 Dans ce cas, le VSPackage est un VSPackage managé installé dans le global assembly cache \(GAC\). Lorsque vous le régénérez pour inclure le correctif de sécurité, vous devez modifier la partie de numéro de révision du numéro de version d’assembly. Les informations d’inscription à l’origine pour le nouveau numéro de version d’assembly remplace la version précédente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour charger l’assembly fixe.  
  
 ![Graphique de mise à jour du package VS côte à côte VS](~/docs/extensibility/internals/media/vs_sbys_packageupdate.gif "VS\_SbyS\_PackageUpdate")  
Programme d’installation de mise à jour côte\-à\-côte VSPackage  
  
 **Remarque** pour plus d’informations sur le déploiement des assemblys côte à côte, consultez [en simplifiant le déploiement et la résolution de l’enfer des DLL avec le .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## Voir aussi  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Prise en charge de plusieurs Versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)