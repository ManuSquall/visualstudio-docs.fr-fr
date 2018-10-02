---
title: La mise à niveau des projets personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: 5c3fd31cfc7cfbf3f7dd687d38483f5bb62703ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503964"
---
# <a name="upgrading-custom-projects"></a>Mise à niveau de projets personnalisés
Si vous modifiez les informations persistantes dans le fichier projet entre des versions Visual Studio différentes de votre produit, vous devez prendre en charge la mise à niveau de votre fichier projet vers la version la plus récente. Pour prendre en charge la mise à niveau qui vous permet de participer les **Assistant Conversion de Visual Studio**, implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface. Cette interface fournit le seul mécanisme disponible pour mettre à niveau une copie. La mise à niveau du projet est une étape du processus d’ouverture de la solution. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface est implémentée par la fabrique de projet ou au moins doit être obtenue à partir de la fabrique de projets.  
  
 L’ancien mécanisme qui utilise le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface est toujours pris en charge, mais conceptuellement met à niveau le système de projet dans le cadre du projet ouvert. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface est donc appelée par le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environnement même si le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface est appelée ou implémentée. Cette approche vous permet d’utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> implémenter la copie et de projeter uniquement les parties de la mise à niveau et de déléguer le reste du travail à effectuer sur place (éventuellement au nouvel emplacement) par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface.  
  
 Pour un exemple d’implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, consultez [exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md).  
  
 Scénarios possibles lors d’une mise à niveau de projet :  
  
-   Si le fichier présente un format récent non pris en charge par le projet, il doit retourner une erreur indiquant ce problème. Cela suppose que la version antérieure de votre produit (par exemple, Visual Studio .NET 2003) inclut le code de vérification de la version.  
  
-   Si le <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> indicateur est spécifié dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> (méthode), la mise à niveau va être implémentée comme une mise à niveau sur place avant l’ouverture du projet.  
  
-   Si le <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> indicateur est spécifié dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> (méthode), la mise à niveau est implémentée comme une mise à niveau de la copie.  
  
-   Si le <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> indicateur est spécifié dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> appeler, puis l’utilisateur a été invité par l’environnement pour mettre à niveau le fichier projet comme une mise à niveau sur place, une fois que le projet est ouvert. Par exemple, l’environnement invite l’utilisateur à effectuer la mise à niveau quand celui-ci ouvre une version antérieure de la solution.  
  
-   Si le <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> indicateur n’est pas spécifié dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> appeler, vous devez inviter l’utilisateur à mettre à niveau le fichier projet.  
  
     Voici un exemple de message d’invite de mise à niveau :  
  
     « Le projet '%1' a été créé avec une version antérieure de Visual Studio. Si vous l’ouvrez avec cette version de Visual Studio, vous ne pourrez peut-être plus l’ouvrir avec les versions antérieures de Visual Studio. Voulez-vous continuer et ouvrir ce projet ? »  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Pour implémenter IVsProjectUpgradeViaFactory  
  
1.  Implémentez la méthode de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> d’interface, en particulier le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> méthode dans votre implémentation de fabrique de projet, ou rendre les implémentations pouvant être appelé à partir de votre implémentation de fabrique de projet.  
  
2.  Si vous souhaitez effectuer une mise à niveau sur place dans le cadre de la solution d’ouverture, spécifiez l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> en tant que le `VSPUVF_FLAGS` paramètre dans votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implémentation.  
  
3.  Si vous souhaitez effectuer une mise à niveau sur place dans le cadre de la solution d’ouverture, spécifiez l’indicateur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> en tant que le `VSPUVF_FLAGS` paramètre dans votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implémentation.  
  
4.  Pour les étapes 2 et 3, le fichier réel étapes mise à niveau, à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, peut être implémenté comme décrit dans la « implémentation `IVsProjectUpgade`» ci-dessous, ou vous pouvez déléguer la mise à niveau de fichier réel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Utilisez les méthodes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> pour valider la mise à niveau des messages pour l’utilisateur à l’aide de l’Assistant de Migration Visual Studio connexes.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> interface est utilisée pour implémenter n’importe quel type de mise à niveau de fichier qui doit se produire dans le cadre de la mise à niveau du projet. Cette interface n’est pas appelée à partir de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, mais n’est fourni comme un mécanisme pour mettre à niveau des fichiers qui font partie du système de projet, mais le système de projet principal n’est peut-être pas directement connaissance. Par exemple, cette situation peut se produire si les fichiers et les propriétés liés au compilateur ne sont pas gérés par la même équipe de développement que celle qui gère le reste du système de projet.  
  
## <a name="ivsprojectupgrade-implementation"></a>Implémentation d’IVsProjectUpgrade  
 Si votre système de projet implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> uniquement, il ne peut pas être utilisé dans le **Assistant Conversion de Visual Studio**. Toutefois, même si vous implémentez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface, vous pouvez déléguer la mise à niveau fichier <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implémentation.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Pour implémenter IVsProjectUpgrade  
  
1.  Lorsqu’un utilisateur tente d’ouvrir un projet, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> méthode est appelée par l’environnement après l’ouverture du projet et avant tout autre utilisateur peut prendre des mesures sur le projet. Si l’utilisateur avait déjà été invité à mettre à niveau de la solution, puis le <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> indicateur est passé dans le `grfUpgradeFlags` paramètre. Si l’utilisateur ouvre un projet directement, ce type comme à l’aide de la **ajouter un projet existant** commande, puis le <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> indicateur n’est pas passé et le projet doit inviter l’utilisateur à mettre à niveau.  
  
2.  En réponse à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> appel, le projet doit évaluer si le fichier projet est mis à niveau. Si le projet n’a pas besoin mettre à niveau le type de projet vers une nouvelle version, il peut simplement retourner la <xref:Microsoft.VisualStudio.VSConstants.S_OK> indicateur.  
  
3.  Si le projet doit mettre à niveau le type de projet vers une nouvelle version, elle doit déterminer si le fichier de projet peut être modifié en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (méthode) et en passant une valeur de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> pour le `rgfQueryEdit` paramètre. Ensuite, le projet doit effectuer les opérations suivantes :  
  
    -   Si le `VSQueryEditResult` valeur retournée dans le `pfEditCanceled` paramètre est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, puis la mise à niveau peut continuer, car le fichier projet peut être écrites.  
  
    -   Si le `VSQueryEditResult` valeur retournée dans le `pfEditCanceled` paramètre est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> et `VSQueryEditResult` valeur a le <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit défini, puis <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> doit retourner une erreur, étant donné que les utilisateurs doivent résoudre les autorisations émettre eux-mêmes. Le projet doit alors effectuer les opérations suivantes :  
  
         Signaler l’erreur à l’utilisateur en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>. et retourner le <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> code d’erreur à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
    -   Si le `VSQueryEditResult` valeur est <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> et `VSQueryEditResultFlags` valeur a le <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit défini, puis le fichier de projet doit être extrait en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4.  Si le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> appel sur le fichier projet entraîne le fichier à extraire et la dernière version à récupérer, puis le projet est déchargé et rechargé. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> méthode est appelée à nouveau une fois qu’une autre instance du projet est créée. À ce deuxième appel, le fichier projet peut être écrit sur le disque. Il est recommandé que le projet enregistre une copie du fichier projet dans le format antérieur avec l’extension de fichier .OLD, qu’il apporte les modifications nécessaires pour la mise à niveau, puis qu’il enregistre le fichier projet dans le nouveau format. Là encore, si une partie de la mise à niveau échoue, la méthode doit indiquer une erreur en retournant <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Le projet est alors déchargé dans l’Explorateur de solutions.  
  
     Il est important de comprendre le processus complet qui se produit dans l’environnement pour le cas dans lequel l’appel à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (méthode) (en spécifiant une valeur de ReportOnly) retourne le <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> et <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> indicateurs.  
  
5.  L’utilisateur tente d’ouvrir le fichier projet.  
  
6.  L’environnement appelle votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implémentation.  
  
7.  Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> retourne `true`, l’environnement appelle votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implémentation.  
  
8.  L’environnement appelle votre <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implémentation pour ouvrir le fichier et initialiser l’objet de projet, par exemple, Projet1.  
  
9. L’environnement appelle votre implémentation d’ `IVsProjectUpgrade::UpgradeProject` pour déterminer si le fichier projet doit être mis à niveau.  
  
10. Vous appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et passer une valeur de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> pour le `rgfQueryEdit` paramètre.  
  
11. Retourne l’environnement <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> pour `VSQueryEditResult` et <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit est défini dans `VSQueryEditResultFlags`.  
  
12. Votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implémentation appelle `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
 Cet appel peut entraîner l’extraction d’une nouvelle copie de votre fichier projet et la récupération de la version la plus récente, ainsi que la nécessité de recharger votre fichier projet. À ce stade, il y a deux cas de figure possibles :  
  
-   Si vous gérez votre propre rechargement du projet, l’environnement appelle votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> mise en œuvre (VSITEMID_ROOT). Quand vous recevez cet appel, rechargez la première instance de votre projet (Projet1) et continuez la mise à niveau de votre fichier projet. L’environnement sait que vous gérez votre propre rechargement du projet si vous retournez `true` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
-   Si vous ne gérez pas votre propre rechargement du projet, puis vous retournez `false` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). Dans ce cas, avant de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True), [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True),) est retournée, l’environnement crée une autre instance de votre projet, Projet2, par exemple, en tant que suit :  
  
    1.  L’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> sur le premier objet de projet, Projet1, ce qui fait passer cet objet à l’état inactif.  
  
    2.  L’environnement appelle votre implémentation d’ `IVsProjectFactory::CreateProject` pour créer une deuxième instance de votre projet (Projet2).  
  
    3.  L’environnement appelle votre implémentation d’ `IPersistFileFormat::Load` pour ouvrir le fichier et initialiser le deuxième objet projet (Projet2).  
  
    4.  L’environnement appelle `IVsProjectUpgrade::UpgradeProject` une deuxième fois pour déterminer si l’objet projet doit être mis à niveau. Toutefois, cet appel est effectué sur la nouvelle instance (la deuxième) du projet, Projet2. Il s’agit du projet qui est ouvert dans la solution.  
  
        > [!NOTE]
        >  Dans l’instance de votre premier projet, Projet1, est placé dans l’état inactif, puis vous devez retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK> du premier appel à votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implémentation. Consultez [projet de base](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) pour une implémentation de `IVsProjectUpgrade::UpgradeProject`.  
  
    5.  Vous appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et passer une valeur de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> pour le `rgfQueryEdit` paramètre.  
  
    6.  Retourne l’environnement <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> et la mise à niveau peut continuer, car le fichier projet peut être écrites.  
  
 Si vous ne parvenez pas à mettre à niveau, retourner <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> de `IVsProjectUpgrade::UpgradeProject`. Si aucune mise à niveau n’est nécessaire ou si vous choisissez de ne pas faire la mise à niveau, gérez l’appel `IVsProjectUpgrade::UpgradeProject` comme une absence d’opération. Si vous retournez <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, un nœud d’espace réservé est ajouté à la solution pour votre projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Conversion de Visual Studio](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [La mise à niveau des éléments de projet](../misc/upgrading-project-items.md)   
 [Projets](../extensibility/internals/projects.md)