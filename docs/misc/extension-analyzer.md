---
title: "Analyseur d’extension | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, analyseur d’échec de chargement"
ms.assetid: 8d2bcc4e-9feb-45a5-8d8e-470346f0d39e
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Analyseur d’extension
L’**analyseur d’extension** capture et enregistre les échecs de chargement d’extensions les plus courants. L’**analyseur d’extension** s’exécute dans sa propre fenêtre d’outil. L’analyseur indique la raison de l’échec et des suggestions sur la façon de résoudre le problème.  
  
 L’[analyseur d’extension](http://go.microsoft.com/fwlink/?LinkId=205840) peut être téléchargé à partir de la galerie Visual Studio. Les assemblys de l’**analyseur d’extension** sont installés dans \<*chemin installation Visual Studio*\> \\Common7\\IDE\\PrivateAssemblies\\.  
  
## Visiteur  
 Après avoir installé l’**analyseur d’extension**, dans le menu **Outils**, cliquez sur **Analyseur d’extension**, puis sur **Navigateur**. Une fenêtre s’affiche et répertorie toutes les extensions qui sont inscrites sur l’ordinateur. Il existe différents onglets pour les fichiers VSIX, les packages Visual Studio, les fichiers PkgDef et les composants MEF. Vous pouvez trier les listes selon les noms des différentes colonnes.  
  
1.  L’onglet VSIX affiche des informations sur les extensions VSIX installées. Vous pouvez inclure des composants système en cochant la case **Afficher les composants système**. Dans cet onglet, vous pouvez accéder aux entrées du journal pour le VSIX, ouvrir le manifeste VSIX dans l’éditeur XML de Visual Studio et ouvrir le dossier où l’extension VSIX est installée.  
  
2.  L’onglet Packages Visual Studio affiche des informations sur les packages Visual Studio actuellement connus de Visual Studio, qu’ils soient ou non chargés. Ces informations incluent l’identificateur VSIX, le fichier .pkgdef et le GUID du package Visual Studio. Vous pouvez inclure les packages Visual Studio système en cochant la case **Afficher les packages système**. Dans cet onglet, vous pouvez accéder aux entrées du journal, afficher les VSIX répertoriés sous l’onglet VSIX, consultez le fichier .pkgdef sous l’onglet Fichiers PkgDef et analyser le package Visual Studio. Les résultats de l’analyse s’affichent dans le volet **Sortie**.  
  
3.  L’onglet Fichiers PkgDef affiche des informations sur les fichiers .pkgdef pour les extensions connues de Visual Studio. Ces informations incluent l’identificateur du VSIX et le chemin de l’extension. Vous pouvez accéder au journal ou à l’onglet VSIX, et vous pouvez afficher le fichier .pkgdef dans l’éditeur.  
  
4.  L’onglet Composants MEF affiche des informations sur les composants MEF qui sont connus de Visual Studio. Ces informations incluent l’identificateur du VSIX et le chemin où l’extension est installée. Vous pouvez inclure des composants système en cochant la case **Afficher les composants système**. Vous pouvez également accéder à l’entrée VSIX correspondante, au fichier .pkgdef et à l’emplacement où l’extension est installée.  
  
> [!WARNING]
>  Vous pouvez recevoir un message vous invitant à activer la journalisation de Fusion. Pour cela, sélectionnez un emplacement pour les fichiers journaux. Vous pouvez être invité à redémarrer toutes les instances de Visual Studio avant de continuer.  
  
## Visionneuse du journal  
 Vous pouvez consulter les messages de journalisation avec la **Visionneuse du journal des extensions** si vous exécutez un projet pour lequel la journalisation est activée \(en ajoutant \/log aux arguments de ligne de commande de votre projet\). Pour plus d'informations, consultez [\/Log](../ide/reference/log-devenv-exe.md). La **Visionneuse du journal des extensions** affiche la date, l’écouteur, le type d’entrée \(type de message\), le type d’erreur, les informations de classe\/interface et le message du journal. Vous pouvez trier et filtrer les informations.  
  
## Problèmes courants de chargement des extensions  
 Voici quelques\-unes des raisons courantes de l’échec de chargement d’une extension dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] :  
  
-   Problèmes de dépendance. Une extension peut avoir été déployée de telle façon que les assemblys dépendants sont introuvables.  
  
-   Exceptions. Quand un package Visual Studio est chargé, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] appelle sa méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>. Si cette méthode lève une exception, le chargement du package Visual Studio échoue. La meilleure façon d’identifier ce problème est de parcourir le code SetSite.  
  
-   Inscription incorrecte. Vérifiez que l’extension est signée de façon appropriée et que le package Visual Studio est inscrit avec la clé publique appropriée.  
  
## Voir aussi  
 [La gestion de packages VS](../extensibility/managing-vspackages.md)