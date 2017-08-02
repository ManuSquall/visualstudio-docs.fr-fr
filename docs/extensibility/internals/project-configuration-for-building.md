---
title: "Configuration de projet pour la cr&#233;ation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuration de Visual Studio SDK, pour la création de projets"
  - "configurations de projet, création"
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Configuration de projet pour la cr&#233;ation
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La liste des configurations de solution pour une solution donnée est gérée par la boîte de dialogue Configurations de Solution.  
  
 Un utilisateur peut créer d'autres configurations de solutions, chacune avec son propre nom unique. Lorsque l'utilisateur crée une nouvelle configuration de solution, l'IDE par défaut le nom de configuration correspondant dans les projets ou le débogage si aucun nom correspondant n'existe. L'utilisateur peut modifier la sélection pour répondre aux besoins spécifiques si nécessaire. La seule exception à ce comportement est lorsque le projet prend en charge une configuration qui correspond au nom de la nouvelle configuration de solution. Par exemple, supposons qu'une solution contenant Project1 et Project2. Project1 possède des configurations de projet Debug, commerciale et MyConfig1. Project2 possède des configurations de projet Debug, commerciale et MyConfig2.  
  
 Si l'utilisateur crée une nouvelle configuration de solution nommée MyConfig2, Project1 lie sa configuration Debug à la configuration de solution par défaut. Project2 lie également sa configuration MyConfig2 à la configuration de solution par défaut.  
  
> [!NOTE]
>  Liaison respecte la casse.  
  
 Lorsque l'utilisateur sélectionne le **sélection Multiple** élément dans la liste déroulante configuration, l'environnement affiche une boîte de dialogue qui fournit la liste des configurations disponibles.  
  
 ![Configurations multiples](~/extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
Plusieurs configurations  
  
 Dans cette boîte de dialogue, l'utilisateur peut sélectionner une ou plusieurs configurations. Une fois sélectionné, les valeurs des propriétés affichées dans la boîte de dialogue des pages de propriétés reflètent l'intersection des valeurs pour les configurations sélectionnées.  
  
 Consultez [Configuration de la solution](../../extensibility/internals/solution-configuration.md) Pour plus d'informations relatives à l'ajout et la modification du nom des configurations pour les projets et solutions.  
  
 Dépendances du projet et l'ordre de génération sont configuration indépendante de la solution : autrement dit, vous pouvez uniquement définir arborescence d'une dépendance pour tous les projets dans la solution. Clic droit sur la solution ou le projet et en sélectionnant le **dépendances du projet** ou **commande de génération de projet** option ouvre le **dépendances du projet** boîte de dialogue. Il peut également être ouvert à partir de la **projet** menu.  
  
 ![Dépendances du projet](~/extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
Dépendances du projet  
  
 Dépendances de projet déterminent l'ordre dans lequel les projets sont générés. Utilisez l'onglet de l'ordre de la génération dans la boîte de dialogue pour afficher l'ordre exact dans lequel les projets dans une solution générer et utilisez l'onglet dépendances pour modifier l'ordre de génération.  
  
> [!NOTE]
>  Dans la liste des projets qui ont leurs cases à cocher activées mais grisées ont été ajoutés par l'environnement en raison des dépendances explicites spécifiées par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> ou le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfaces et ne peut pas être modifié. Par exemple, ajoutez une référence de projet dans un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projet vers un autre projet ajoute automatiquement une dépendance de génération qui ne peut être supprimée en supprimant la référence. Impossible de sélectionner les projets dont les cases à cocher sont désactivées et apparaissent grisés car cela créerait une boucle de dépendance \(par exemple, Project1 serait dépendant Project2 et Project2 serait dépendant Project1\), ce qui serait bloquer la génération.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] processus de génération incluent la compilation classique et les opérations de liaison qui sont appelées avec une seule commande de génération. Deux autres processus de génération peuvent également être pris en charge : une opération de nettoyage pour supprimer tous les éléments de sortie à une version antérieure et une vérification à jour pour déterminer si un élément de sortie dans une configuration a changé.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> objets de retournent un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> \(renvoyé par <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>\) pour gérer leurs processus de génération. Pour signaler l'état d'une opération de génération lorsqu'elle se produit, les configurations effectuent des appels vers <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, une interface implémentée par l'environnement et tout autre objet intéressés des événements d'état de build.  
  
 Une fois créé, les paramètres de configuration peuvent servir à déterminer si elles peuvent être exécutées sous le contrôle du débogueur. Implémentent des configurations <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> pour prendre en charge le débogage.  
  
 Après avoir implémenté les dépendances du projet, vous pouvez manipuler par programmation les dépendances via le modèle automation. Vous appelez <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> dans le modèle automation. Il n'existe aucune interface de niveau API VSIP disponibles qui permettent la manipulation directe des configurations manager de la solution et leurs propriétés.  
  
 En outre, vous pouvez fournir une grille dans la fenêtre de dépendances du projet. Pour plus d'informations, consultez [Afficher la grille Propriétés](../../extensibility/internals/properties-display-grid.md).  
  
## Voir aussi  
 [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md)   
 [Configuration de projet pour la gestion du déploiement](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)