---
title: Manifestes d’application pour les solutions Office
description: Découvrez comment un manifeste d’application est un fichier XML qui décrit les assemblys qui sont chargés dans une solution Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a16d0f438d06cbfa48538bb3e370ed9b334ad16
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847921"
---
# <a name="application-manifests-for-office-solutions"></a>Manifestes d’application pour les solutions Office
  Un manifeste d’application est un fichier XML qui décrit les assemblys qui sont chargés dans une solution Microsoft Office. Les outils de développement Microsoft Office dans Visual Studio utilisent le [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] schéma de manifeste d’application défini dans la référence du manifeste de l' [application ClickOnce](../deployment/clickonce-application-manifest.md) .

 Les manifestes d’application pour solutions Office utilisent les éléments et les attributs [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] suivants.

|Élément|Description|Attributs|
|-------------|-----------------|----------------|
|[&#60;élément&#62; de l’assembly &#40;application ClickOnce&#41;](../deployment/assembly-element-clickonce-deployment.md)|Obligatoire. Élément de niveau supérieur.|**manifestVersion**|
|[&#60;élément assemblyIdentity&#62; &#40;application ClickOnce&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|Obligatoire. Identifie l’assembly principal de l’application [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .|**name**<br /><br /> **version**<br /><br /> **publicKeyToken**<br /><br /> **processorArchitecture**<br /><br /> **language**|
|[&#60;élément trustInfo&#62; &#40;application ClickOnce&#41;](../deployment/trustinfo-element-clickonce-application.md)|Identifie les exigences de sécurité de l’application.|Aucun|
|[&#60;élément entryPoint&#62; &#40;application ClickOnce&#41;](../deployment/entrypoint-element-clickonce-application.md)|Obligatoire. Identifie le point d’entrée de code d’application pour l’exécution.|**name**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|
|[&#60;élément de&#62; de dépendance &#40;application ClickOnce&#41;](../deployment/dependency-element-clickonce-deployment.md)|Obligatoire. Identifie chaque dépendance requise pour l’exécution de l’application. Identifie éventuellement les assemblys qui doivent être préinstallés.|Aucun|
|[&#60;&#62; élément de fichier &#40;application ClickOnce&#41;](../deployment/file-element-clickonce-application.md)|Obligatoire. Identifie chaque fichier non assembly utilisé par l’application. Peut inclure les données d’isolation COM (Component Object Model) associées au fichier.|**name**<br /><br /> **size**|

 Les manifestes d’application pour solutions Office disposent de l’élément suivant dans l’espace de noms `co.v1` .

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

 Ces manifestes d’application disposent aussi des éléments et attributs suivants dans l’espace de noms `vstav3` .

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customizations>
      <customization>
      </customization>
    </customizations>
  </application
</addIn>
```

|Élément|Description|Attributs|
|-------------|-----------------|----------------|
|[&#60;élément customHostSpecified&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Obligatoire. Marque le manifeste précisément comme une solution Office.|Aucun|
|[&#60;élément AddIn&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Obligatoire. Stocke les points d’entrée dans un espace de noms unique.|Aucun|
|[&#60;élément entryPointsCollection&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Obligatoire. Regroupe tous les assemblys pour une ou plusieurs solutions Office.|**id**|
|[&#60;élément entryPoints&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Obligatoire. Regroupe tous les assemblys pour exécuter une solution Office.|Aucun|
|[&#60;élément entryPoint&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Obligatoire. Identifie l’assembly à exécuter dans une solution Office.|**class**<br /><br /> **façon**|
|[&#60;mettre à jour&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Obligatoire. Configure les mises à jour pour la solution.|**activé**<br /><br /> **expiration**|
|[&#60;élément postActions&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|facultatif. Regroupe toutes les actions de post-déploiement qui s’exécutent après l’installation des solutions Office.|Aucun|
|[&#60;élément postAction&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|facultatif. Identifie une action de post-déploiement.|Aucun|
|[&#60;élément postActionData&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|facultatif. Configure les données pour une action de post-déploiement.|Aucun|
|[&#60;élément d'&#62; d’application &#40;développement Office dans Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Obligatoire. Encapsule les informations spécifiques à l’application dans un même nœud.|Aucun|
|[&#60;les personnalisations&#62; élément &#40;le développement Office dans Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Obligatoire. Stocke toutes les informations spécifiques à l’hôte de l’application dans un espace de noms distinct.|Aucun|
|[&#60;&#62; élément de personnalisation &#40;développement Office dans Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Obligatoire. Stocke les informations spécifiques à l’hôte de l’application dans un espace de noms distinct.|**xmlns**|
|[&#60;document&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Obligatoire uniquement pour les solutions au niveau du document. Stocke les informations spécifiques à la personnalisation.|**solutionId**|
|[&#60;élément appAddin&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Obligatoire uniquement pour les solutions au niveau de l’application. Stocke les informations spécifiques à la personnalisation.|**application**<br /><br /> **loadBehavior**<br /><br /> **keyName**|
|[&#60;l’élément&#62; friendlyName &#40;développement Office dans Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|facultatif. Stocke le nom du complément VSTO qui figure dans la liste des compléments VSTO installés.|Aucun|
|[&#60;Description&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Obligatoire uniquement pour les compléments VSTO. Stocke la description qui s’affiche dans la liste des programmes installés.|Aucun|
|[&#60;formRegions&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Obligatoire uniquement pour les compléments VSTO Outlook qui comprennent des zones de formulaire.|Aucun|
|[&#60;formRegion&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Obligatoire uniquement pour les compléments VSTO Outlook qui comprennent des zones de formulaire.|**Nom**|
|[&#60;élément vstoRuntime&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Obligatoire. Décrit la version spécifique de Visual Studio Tools pour Office Runtime qui est prise en charge par la solution Office.|**3/05**<br /><br /> **version**<br /><br /> **supportUrl**|

## <a name="remarks"></a>Remarques
 Vous pouvez modifier manuellement les manifestes d’application et de déploiement dans les solutions Office. Ensuite, vous devez signer à nouveau les manifestes d’application et de déploiement à l’aide de l’Outil Manifest Generation and Editing (*mage.exe* et *mageui.exe*). Pour plus d’informations, consultez [Comment : signer à nouveau les manifestes d’application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="file-location"></a>Emplacement du fichier
 Un manifeste d’application est propre à une seule version d’une solution. Pour cette raison, les manifestes d’application doivent être stockés à l’écart des manifestes de déploiement. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] place les fichiers spécifiques à la version dans un sous-répertoire nommé d’après la version associée dans le sous-répertoire des *fichiers d’application* du dossier de publication.

## <a name="file-name-syntax"></a>Syntaxe du nom de fichier
 Le nom d’un fichier manifeste d’application doit être le nom complet et l’extension de l’application, tel qu’il est identifié dans l’élément **assemblyIdentity** , suivi de l’extension *. manifest*. Par exemple, un manifeste d’application qui fait référence à la personnalisation de *OutlookAddIn1.dll* utilise la syntaxe de nom de fichier suivante.

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>Voir aussi

- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)