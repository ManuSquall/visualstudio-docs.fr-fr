---
title: "Vue d&#39;ensemble de la couleur et de police | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), la police et couleur"
  - "police et couleur de contrôle (Visual Studio SDK), les éditeurs"
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Vue d&#39;ensemble de la couleur et de police
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique traite de la police et les paramètres de couleur de texte dans l'environnement de développement intégré \(IDE\) de \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Elle présente également les concepts des catégories et des éléments d'affichage, et elle décrit comment les VSPackages et l'éditeur principal utilisent des attributs de texte.  
  
## les polices et la page de propriétés de couleurs  
 Vous pouvez gérer les attributs de texte dans l'environnement de développement intégré \(IDE\) de \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] via la page de propriétés de **Polices et couleurs** .  Pour rechercher la page de propriétés de **Polices et couleurs** , dans le menu d' **Outils** , cliquez sur **Options**.  Développez **Environnement**, puis cliquez sur **Polices et couleurs**.  
  
## catégories et éléments d'affichage  
 Les polices et les couleurs sont organisées en **Catégories** et **Éléments affichés**.  
  
-   **Category** est un conteneur logique ou fonctionnel pour un certain nombre d' **Éléments affichés**.  
  
     une liste de **Catégories** est dans la zone déroulante d' **Afficher les paramètres de** de la page de propriétés de **Polices et couleurs** .  
  
-   **élément d'affichage** est une entité bien définie de texte par exemple un commentaire, une chaîne, ou une structure de contrôle qui doit sont colorisés une fois affiche.  
  
 Chaque **élément d'affichage** est défini uniquement dans **Category** qui le contient.  Par conséquent, plusieurs **Category** peut avoir **élément d'affichage** avec le même nom.  
  
## Contrôle d'un VSPackage les polices et de couleurs  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] permet VSPackages à :  
  
-   Définissez la police et de couleur **Catégories**.  
  
-   spécifiez les polices et les couleurs utilisées pour présenter **Éléments affichés**.  
  
-   Interagir avec la page de propriétés de **Polices et couleurs** .  
  
-   Plusieurs **Catégories** global en groupes.  
  
-   Conserver les modifications des paramètres par défaut.  
  
 Il existe deux façons d'interagir avec la police et les sélections des couleurs dans [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
-   Une méthode est connu sous le nom *de la coloration de syntaxe*.  Il est utilisé par un VSPackage qui personnalise l'éditeur existant de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour implémenter un service de langage et créer un éditeur de code source.  
  
     Un seul **Category** prend en charge ce mécanisme, à savoir, **Éditeur de texte**.  
  
-   Une alternative plus générale prend en charge tous les autres **Catégories** et composants d'interface utilisateur autre que l'éditeur de code source lorsque vous affichez le texte.  Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## Paramètres principaux de texte de l'éditeur  
 La police et les paramètres de couleurs pour l'éditeur principal d'un objet de service de langage est régi par **Éditeur de texteCategory** recherche dans la zone déroulante d' **Afficher les paramètres de** de la page de propriétés de **Polices et couleurs** .  
  
 Lorsque vous travaillez avec des éditeurs, vous devez utiliser le mécanisme spécialisée de police et de contrôle des couleurs que le service de langage le fournit pour contrôler et d'étendre les paramètres d' **Éditeur de texte** .  Le mécanisme s'agit *de la coloration de syntaxe* et fournit :  
  
-   une technique simplifiée pour gérer les polices et les couleurs des éléments d'affichage.  
  
     Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
-   Un mécanisme bien défini et optimisé de la colorisation.  
  
     Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
-   La capacité à chacun des deux utilisent les éléments prédéfinis d'affichage d' **Éditeur de texteCategory** et les étendre.  
  
     Pour plus d'informations, consultez [Comment : utiliser des éléments coloriable intégrés](../extensibility/internals/how-to-use-built-in-colorable-items.md) et [Éléments coloriable personnalisés](../extensibility/internals/custom-colorable-items.md).  
  
-   Persistance automatique de l'état actuel de l'élément et des éléments personnalisés d'affichage à la catégorie d' **Éditeur de texte** .  
  
 Pour plus d'informations sur la coloration de syntaxe consultez [Couleurs de syntaxe dans un Service de langage hérité](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## Voir aussi  
 [Interfaces héritées dans l’éditeur](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Couleurs de syntaxe dans un Service de langage hérité](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)