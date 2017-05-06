---
title: "Manifestes d&#39;application pour les solutions Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "manifestes d'application (développement Office dans Visual Studio)"
ms.assetid: dd38685f-f429-4a35-8c11-a03372c9770a
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Manifestes d&#39;application pour les solutions Office
  Un manifeste d’application est un fichier XML qui décrit les assemblys qui sont chargés dans une solution Microsoft Office. Dans Visual Studio, les outils de développement Microsoft Office utilisent le [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]schéma de manifeste d’application défini dans la référence [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
 Les manifestes d’application pour solutions Office utilisent les éléments et les attributs [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] suivants.  
  
|Élément|Description|Attributs|  
|-------------|-----------------|---------------|  
|[&#60;assembly&#62; Element &#40;ClickOnce Application&#41;](~/deployment/assembly-element-clickonce-application.md)|Obligatoire. Élément de niveau supérieur.|`manifestVersion`|  
|[&#60;assemblyIdentity&#62; Element &#40;ClickOnce Application&#41;](~/deployment/assemblyidentity-element-clickonce-application.md)|Obligatoire. Identifie l’assembly principal de l’application [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[&#60;trustInfo&#62; Element &#40;ClickOnce Application&#41;](~/deployment/trustinfo-element-clickonce-application.md)|Identifie les exigences de sécurité de l’application.|None|  
|[&#60;entryPoint&#62; Element &#40;ClickOnce Application&#41;](~/deployment/entrypoint-element-clickonce-application.md)|Obligatoire. Identifie le point d’entrée de code d’application pour l’exécution.|`name`<br /><br /> `dependencyName`<br /><br /> `customHostSpecified`|  
|[&#60;dependency&#62; Element &#40;ClickOnce Application&#41;](~/deployment/dependency-element-clickonce-application.md)|Obligatoire. Identifie chaque dépendance requise pour l’exécution de l’application. Identifie éventuellement les assemblys qui doivent être préinstallés.|Aucun|  
|[&#60;file&#62; Element &#40;ClickOnce Application&#41;](http://msdn.microsoft.com/library/56e3490c-eed5-4841-b1bf-eefe778b6ac9)|Obligatoire. Identifie chaque fichier non assembly utilisé par l’application. Peut inclure les données d’isolation COM \(Component Object Model\) associées au fichier.|`name`<br /><br /> `size`|  
  
 Les manifestes d’application pour solutions Office disposent de l’élément suivant dans l’espace de noms `co.v1`.  
  
```  
<entryPoint> <co.v1:customHostSpecified /> </entryPoint>   
```  
  
 Ces manifestes d’application disposent aussi des éléments et attributs suivants dans l’espace de noms `vstav3`.  
  
```  
<addIn> <entryPointsCollection> <entryPoints> <entryPoint> </entryPoint> </entryPoints> </entryPointsCollection> <update></update> <postActions> <postAction> <postActionData> </postActionData> <postAction> </postActions> <application> <customizations> <customization> </customization> </customizations> </application </addIn>  
```  
  
|Élément|Description|Attributs|  
|-------------|-----------------|---------------|  
|[&#60;customHostSpecified&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Obligatoire. Marque le manifeste précisément comme une solution Office.|None|  
|[Élément &#60;addIn&#62; &#40;Développement Office dans Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Obligatoire. Stocke les points d’entrée dans un espace de noms unique.|Aucun|  
|[&#60;entryPoint&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Obligatoire. Regroupe tous les assemblys pour une ou plusieurs solutions Office.|`id`|  
|[Élément &#60;entryPoint&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Obligatoire. Regroupe tous les assemblys pour exécuter une solution Office.|None|  
|[&#60;entryPoint&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Obligatoire. Identifie l’assembly à exécuter dans une solution Office.|`class`<br /><br /> `contract`|  
|[&#60;update&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Obligatoire. Configure les mises à jour pour la solution.|`enabled`<br /><br /> `expiration`|  
|[Élément &#60;postActions&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Facultatif. Regroupe toutes les actions de post\-déploiement qui s’exécutent après l’installation des solutions Office.|Aucun|  
|[Élément &#60;postAction&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Facultatif. Identifie une action de post\-déploiement.|Aucun|  
|[&#60;postActionData&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Facultatif. Configure les données pour une action de post\-déploiement.|None|  
|[Élément &#60;application&#62; &#40;Développement Office dans Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Obligatoire. Encapsule les informations spécifiques à l’application dans un même nœud.|Aucun|  
|[&#60;customizations&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Obligatoire. Stocke toutes les informations spécifiques à l’hôte de l’application dans un espace de noms distinct.|Aucun|  
|[Élément &#60;customization&#62; &#40;Développement Office dans Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Obligatoire. Stocke les informations spécifiques à l’hôte de l’application dans un espace de noms distinct.|`xmlns`|  
|[&#60;document&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Obligatoire uniquement pour les solutions au niveau du document. Stocke les informations spécifiques à la personnalisation.|`solutionId`|  
|[Élément &#60;appAddin&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Obligatoire uniquement pour les solutions au niveau de l’application. Stocke les informations spécifiques à la personnalisation.|`application`<br /><br /> `loadBehavior`<br /><br /> `keyName`|  
|[&#60;friendlyName&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Facultatif. Stocke le nom du complément VSTO qui figure dans la liste des compléments VSTO installés.|Aucun|  
|[&#60;description&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Obligatoire uniquement pour les compléments VSTO. Stocke la description qui figure dans la liste des programmes installés.|Aucun|  
|[Élément &#60;formRegions&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Obligatoire uniquement pour les compléments VSTO Outlook qui comprennent des zones de formulaire.|None|  
|[&#60;formRegion&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Obligatoire uniquement pour les compléments VSTO Outlook qui comprennent des zones de formulaire.|`Name`|  
|[&#60;vstoRuntime&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Obligatoire. Décrit la version spécifique de Visual Studio Tools pour Office Runtime qui est prise en charge par la solution Office.|`release`<br /><br /> `version`<br /><br /> `supportUrl`|  
  
## Notes  
 Vous pouvez modifier manuellement les manifestes d’application et de déploiement dans les solutions Office. Après quoi, vous devez signer à nouveau les manifestes d’application et de déploiement à l’aide de l’outil Manifest Generation and Editing \(mage.exe et mageui.exe\). Pour plus d'informations, consultez [How to: Re-sign Application and Deployment Manifests](~/deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Emplacement du fichier  
 Un manifeste d’application est propre à une seule version d’une solution. Pour cette raison, les manifestes d’application doivent être stockés à l’écart des manifestes de déploiement.[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] place les fichiers spécifiques à la version dans un sous\-répertoire qui reprend le nom de la version associée dans le sous\-répertoire **Fichiers d’application** du dossier de publication.  
  
## Syntaxe du nom de fichier  
 Le nom d’un fichier de manifeste d’application doit reprendre le nom complet et l’extension de l’application telle qu’identifiée dans l’élément `assemblyIdentity`, suivi de l’extension .manifest. Par exemple, un manifeste d’application qui ferait référence à la personnalisation OutlookAddIn1.dll aurait la syntaxe suivante.  
  
 `OutlookAddIn1.dll.manifest`  
  
## Voir aussi  
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  