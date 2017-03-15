---
title: "Fonctionnement de Graphics Diagnostics | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ae14497-c77c-4399-bc0c-595caba23656
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "mithom"
manager: "douge"
---
# Fonctionnement de Graphics Diagnostics
Insérez l'introduction ici.  
  
## Fonctionnement de Graphics Diagnostics  
 Pour utiliser Graphics Diagnostics, vous devez commencer par enregistrer des informations sur la façon dont une application utilise l'API de Direct3D lorsqu'elle s'exécute, puis examiner ensuite le comportement enregistré.  Pour les frames spécifiés, les informations qui sont enregistrées incluent les appels d'API \(tels que celles qui effacent l'écran, dessinent une géométrie, distribuent des nuanceurs de calcul ou modifient l'état du périphérique graphique\) avec leurs arguments, et copient des tampons et des objets référencés indirectement.  En outre, les appels d'API liés à l'installation et à l'initialisation sont enregistrés avant que les frames soient affichés.  Les informations enregistrées sont écrites dans un fichier du *journal de graphisme* \(.vsglog\).  
  
 Vous devez recréer le comportement de rendu qui est enregistré dans le journal de graphisme en lisant les événements de graphisme sur votre ordinateur de développement, ou sur un ordinateur distant ou un périphérique.  L'ordinateur de lecture peut être le même ordinateur ou le même périphérique que celui où le journal de graphisme a été initialement capturé ou un autre.  Pour la plupart des fonctionnalités de lecture, le matériel graphique de l'ordinateur de lecture est utilisé pour lire les événements de graphiques, mais lorsque le débogueur HLSL est utilisé, le code de nuanceur est toujours lu à l'aide d'un GPU émulé sur l'UC.  L'utilisation d'un GPU émulé permet de parcourir le code de nuanceur, d'inspecter des variables, et d'utiliser d'autres fonctionnalités de débogage courantes que le matériel graphique de l'ordinateur de lecture prenne en charge le débogage du matériel ou non.  
  
> [!NOTE]
>  Bien qu'un journal de graphisme capture la plupart des informations pertinentes en interne, des informations supplémentaires sont requises pour utiliser pleinement certaines fonctionnalités de Graphics Diagnostics.  Par exemple, pour utiliser pleinement la fonctionnalité de pile des appels de graphiques, vous devez également disposer du fichier de base de données du programme \(.pdb\) et du code source de l'application.  Pour déboguer le code source du nuanceur HLSL, vous devez également avoir le code source du nuanceur.  \(Si le nuanceur est compilé à l'aide du compilateur de nuanceur D3D11.1, alors que les informations de débogage sont activées, le code source du nuanceur est incorporé dans le journal de graphisme pendant la capture.\)  
  
> [!NOTE]
>  Compte tenu de la possible indisponibilité de certaines API dans les versions précédentes de Windows ou DirectX, vous ne pouvez pas lire les journaux de graphisme qui ont capturé ces appels d'API sur un ordinateur de lecture qui ne les prend pas en charge.  
  
### Journaux de graphisme  
 Un journal de graphisme contient un ou plusieurs frames qui ont été capturés à partir d'une application graphique DirectX en cours d'exécution.  Comme un journal de graphisme est autonome, ces frames peuvent être recréés ultérieurement, sans informations externes ni références.  Cela signifie que vous pouvez partager des journaux de graphisme avec d'autres développeurs, examiner les problèmes sur des ordinateurs différents, et consulter les journaux de graphisme anciens même si les schémas et les textures ont été modifiés dans le développement.  Vous pouvez aussi charger plusieurs fichiers du journal de graphisme \(.vsglog\) en même temps pour comparer les données et les résultats de rendu.  
  
##### Pour ouvrir un fichier journal de graphisme \(vsglog\)  
  
1.  Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Fichier**.  La boîte de dialogue **Ouvrir un fichier** s'affiche.  
  
2.  Spécifiez un fichier journal de graphisme \(.vsglog\) à ouvrir, puis choisissez le bouton **Ouvrir**.  
  
> [!NOTE]
>  Vous pouvez extraire, modifier, puis enregistrer des copies des maillages et des textures d'un journal de graphisme à l'aide des outils graphiques qui font partie de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Toutefois, le contenu du journal de graphisme n'est pas affecté par ces modifications.  Pour plus d'informations sur ces outils graphiques, voir [Utilisation de ressources 3D pour les jeux et les applications](../designers/working-with-3-d-assets-for-games-and-apps.md).