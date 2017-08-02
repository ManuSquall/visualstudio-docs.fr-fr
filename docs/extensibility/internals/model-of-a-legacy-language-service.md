---
title: "Mod&#232;le d’un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "les services de langage, modèle"
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Mod&#232;le d’un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un service de langage définit les éléments et les fonctionnalités pour une langue spécifique, et est utilisé pour fournir à l'éditeur le informations spécifiques à ce langage.  par exemple, l'éditeur doit connaître les éléments et les mots clés du langage afin de prendre en charge la coloration de syntaxe.  
  
 Le service de langage fonctionne étroitement avec la mémoire tampon de texte gérée par l'éditeur et la vue qui contient l'éditeur.  L'option Microsoft Intellisense **Informations rapides** est un exemple d'une fonctionnalité fournie par un service de langage.  
  
## Un service de langage minimal  
 Le service de langage le plus basique contient les deux objets suivants :  
  
-   *Le service de langage* implémente l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .  Un service de langage contient des informations sur le langage, y compris son nom, extensions de nom de fichier, gestionnaire de fenêtre de code, et coloriseur.  
  
-   *le coloriseur* implémente l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> .  
  
 Le dessin conceptuel suivant affiche un modèle d'un service de langage de base.  
  
 ![Graphique du modèle de service de langage](~/extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Modèle de base de service de langage  
  
 La fenêtre de document héberge *la vue du document* de l'éditeur, auquel cas l'éditeur principal de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  La vue du document et la mémoire tampon de texte sont détenues par l'éditeur.  Ces objets fonctionnent avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] via une fenêtre de document spécialisée appelée *une fenêtre de code*.  La fenêtre de code est contenue dans un objet d'<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> créé et contrôlé par l'IDE.  
  
 Lorsqu'un fichier avec une extension donnée est chargé, l'éditeur ne trouve le service de langage associé à cette extension et passe à lui la fenêtre de code en appelant la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> .  Le service de langage retourne *un gestionnaire de fenêtre de code*, qui implémente l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> .  
  
 Le tableau suivant fournit une vue d'ensemble des objets dans le modèle.  
  
|Composant|Objet|Fonction|  
|---------------|-----------|--------------|  
|mémoire tampon de texte|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Un flux de texte en lecture\/écriture Unicode.  il est possible que le texte utilise d'autres encodages.|  
|fenêtre de code|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Une fenêtre de document qui contient un ou plusieurs vues de texte.  Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se trouve en mode \(MDI\) interface multidocument, la fenêtre de code est un enfant MDI.|  
|affichage de texte|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Une fenêtre qui permet à l'utilisateur de naviguer et pour afficher du texte à l'aide de le clavier et de la souris.  un affichage de texte apparaît à l'utilisateur comme éditeur.  Vous pouvez utiliser des affichages de texte dans les fenêtres ordinaires d'éditeur, la fenêtre Sortie, et la fenêtre exécution.  En outre, vous pouvez configurer un ou de plusieurs affichages de texte d'une fenêtre de code.|  
|Texte le gestionnaire|Géré par le service d' <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> , dans lequel vous obtenez un pointeur d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>|Un composant qui gère des informations communes partagées par tous les composants décrits précédemment.|  
|Service de langage|Dépend de l'implémentation ; implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Un objet qui fournit l'éditeur des informations spécifiques au langage telles que la syntaxe de mise en surbrillance, saisie semi\-automatique des instructions, et accolades correspondantes.|  
  
## Voir aussi  
 [Données de documents et affichage de documents dans les éditeurs personnalisés](../../extensibility/document-data-and-document-view-in-custom-editors.md)