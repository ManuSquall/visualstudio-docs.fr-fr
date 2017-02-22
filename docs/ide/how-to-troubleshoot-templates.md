---
title: "Comment&#160;: d&#233;panner des mod&#232;les | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèles Visual Studio, dépanner"
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Comment&#160;: d&#233;panner des mod&#232;les
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

S'il est impossible de charger un modèle dans l'environnement de développement, il y a plusieurs manières de localiser le problème.  
  
## Validation du fichier .vstemplate  
 Si le fichier .vstemplate d'un modèle n'adhère pas au schéma de modèle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], il se peut que le modèle n'apparaisse pas dans la boîte de dialogue **Nouveau projet**.  
  
#### Pour valider le fichier .vstemplate  
  
1.  Localisez le fichier .zip qui contient le modèle.  
  
2.  Extrayez le fichier .zip.  
  
3.  Dans le menu **Fichier** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], cliquez sur **Ouvrir**, puis sur **Fichier**.  
  
4.  Sélectionnez le fichier .vstemplate du modèle et cliquez sur **Ouvrir**.  
  
5.  Vérifiez que le XML du fichier .vstemplate adhère au schéma de modèle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Pour plus d'informations sur le schéma .vstemplate, consultez [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
    > [!NOTE]
    >  Pour obtenir une aide IntelliSense lorsque vous créez le fichier .vstemplate, ajoutez un attribut `xmlns` à l'élément `VSTemplate` et assignez\-lui la valeur http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005.  
  
6.  Enregistrez et fermez le fichier .vstemplate.  
  
7.  Sélectionnez les fichiers inclus dans votre modèle, cliquez avec le bouton droit, sélectionnez **Envoyer vers** et cliquez sur **Dossier compressé** \(dossier zippé\).  Les fichiers que vous avez sélectionnés sont compressés dans un fichier .zip.  
  
8.  Placez le nouveau fichier .zip dans le même répertoire que l'ancien fichier .zip.  
  
9. Supprimez les fichiers de modèles extraits et l'ancien fichier .zip du modèle.  
  
## Analyse du journal des événements  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] enregistre les erreurs rencontrées lors du traitement des fichiers .zip du modèle.  Si un modèle n'apparaît pas dans la boîte de dialogue **Nouveau projet** comme prévu, vous pouvez utiliser l'**Observateur d'événements** pour résoudre le problème.  
  
#### Pour localiser des erreurs de modèle dans l'Observateur d'événements  
  
1.  Dans Windows, cliquez sur **Démarrer**, cliquez sur **Panneau de configuration**, double\-cliquez sur **Outils d'administration**, puis double\-cliquez sur **Observateur d'événements**.  
  
2.  Dans le volet de gauche, cliquez sur **Application**.  
  
3.  Recherchez des événements dont la **Source** a la valeur `Visual Studio - VsTemplate`.  
  
4.  Double\-cliquez sur un événement de modèle pour afficher l'erreur.  
  
## Voir aussi  
 [Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)