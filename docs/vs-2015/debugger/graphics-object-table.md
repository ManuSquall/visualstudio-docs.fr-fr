---
title: Table des objets Graphics | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 86279ff4e1721007814163787bd9ed06edc9fb13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161176"
---
# <a name="graphics-object-table"></a>Table des objets Graphics
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La Table des objets Graphics dans Visual Studio Graphics Analysis vous permet d'identifier les objets Direct3D qui prennent en charge un frame de votre jeu ou application.  
  
 Voici la Table des objets :  
  
 ![Objets Direct3D ayant été créés par une application.](../debugger/media/gfx-diag-demo-object-table-orientation.png "gfx_diag_demo_object_table_orientation")  
  
## <a name="understanding-the-graphics-object-table"></a>Présentation de la Table des objets Graphics  
 À l'aide de la Table des objets, vous pouvez analyser les objets Direct3D qui prennent en charge le rendu d'un frame particulier. Vous pouvez identifier un problème de rendu pour un objet spécifique en examinant ses propriétés et ses données (à l’aide d’autres outils de Graphics Diagnostics précédemment dans votre diagnostic, vous pouvez limiter la liste des objets qui ne sont pas conformes à vos attentes). Une fois que vous avez trouvé l’objet incriminé, vous pouvez utiliser une visualisation spécifique à son type pour l’examiner (par exemple, vous pouvez utiliser l’éditeur d’images pour afficher des textures ou le *visualiseur de mémoire tampon* pour afficher le contenu de la mémoire tampon).  
  
 La Table des objets prend en charge le copier-coller, ce qui vous permet d'utiliser un autre outil (par exemple Microsoft Excel) pour examiner son contenu.  
  
### <a name="graphics-object-table-format"></a>Format de la Table des objets Graphics  
 La Table des objets affiche les objets et ressources Direct3D qui prennent en charge le frame associé à l'événement sélectionné, par exemple, les objets d'état, les mémoires tampons, les nuanceurs, les textures et d'autres ressources. Les objets créés dans un frame précédent, mais qui ne sont pas utilisés dans le frame capturé sont omis de la table des objets. Les objets détruits par des événements précédents dans le frame capturé sont omis dans les événements postérieurs. Les objets qui ne sont pas définis dans D3D10Device ou D3D11DeviceContext sont affichés sous forme de texte grisé. Les objets sont affichés sous forme de tableau.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Identificateur**|ID de l'objet.|  
|**Name**|Informations spécifiques à l'application, qui ont été définies sur l'objet à l'aide de la fonction Direct3D `SetPrivateData` (en règle générale, pour fournir des informations d'identification supplémentaires sur un objet).|  
|**Type**|Type d'objet.|  
|**Actif**|Affiche « * » pour un objet défini sur D3D10Device ou D3D11DeviceContext dans le frame capturé.<br /><br /> Cela correspond aux objets affichés sous forme de texte grisé. Une entrée de colonne est fournie pour vous permettre de trier la table d'objets.|  
|**Taille**|Taille de l'objet en octets.|  
|**Format**|Format de l'objet. Par exemple, format d'un objet de texture ou modèle de nuanceur d'un objet de nuanceur.|  
|**Width**|Largeur d'un objet de texture. Ne s'applique pas aux autres types d'objet.|  
|**Height**|Hauteur d'un objet de texture. Ne s'applique pas aux autres types d'objet.|  
|**Profondeur**|Profondeur d'un objet de texture 3D. Si une texture n'est pas 3D, la valeur est 0. Ne s'applique pas aux autres types d'objet.|  
|**Mips**|Nombre de niveaux MIP d'un objet de texture. Ne s'applique pas aux autres types d'objet.|  
|**ArraySize**|Nombre de textures dans un tableau de textures. La plage va de 1 à une limite supérieure définie par le niveau de fonctionnalité actuel. Pour un mappage de cube, cette valeur représente 6 fois le nombre de mappages de cube dans le tableau.|  
|**Exemples**|Nombre d'échantillons multiples par pixel.|  
  
## <a name="graphics-object-viewers"></a>Visionneuses d'objets Graphics  
 Pour afficher les détails d'un objet, ouvrez-le en choisissant son nom dans la Table des objets. Les détails de l'objet sont affichés dans différents formats, en fonction de son type. Par exemple, les textures sont affichées à l'aide de la visionneuse de textures. En outre, l'état du périphérique, tel que le contexte de périphérique D3D11, s'affiche en tant que liste mise en forme. Les différentes versions de Direct3D utilisent différents objets. Par ailleurs, il existe souvent des visualiseurs spécifiques pour les objets les plus importants de chaque version.  
  
 Voici la visionneuse de textures affichant le contenu de l'étape de canalisation Fusion de sortie.  
  
 ![Aperçu de texture affichant la fusion de sortie](../debugger/media/gfx-diag-texture-preview.png "gfx_diag_texture_preview")  
  
### <a name="d3d12-command-list"></a>Liste des commandes D3D12  
 Dans Direct3D 12, une liste de commandes est un objet qui enregistre les commandes dans un allocateur de commandes pour qu'elles puissent être envoyées au GPU sous forme de requête unique. Les listes de commandes effectuent généralement une série de commandes de définition d'état, de dessin, d'effacement et de copie. Elles sont particulièrement importantes, car elles représentent la méthode de rendu par défaut dans Direct3D 12. En outre, elles peuvent être réutilisées entre les frames pour contribuer à l'amélioration des performances. Les détails spécifiques aux listes de commandes sont affichés dans une nouvelle fenêtre de document, avec les informations relatives à chaque étape de canalisation présentées sous leur propre onglet.  
  
### <a name="d3d12-pipeline-state-object-pso"></a>Objet État du pipeline D3D12  
 Dans Direct3D 12 un objet État du pipeline représente une partie significative de l'état du GPU. Il comprend notamment tous les nuanceurs actuellement définis et certains objets d'état de fonction fixe. Une fois créé, un objet État du pipeline est immuable, une application peut uniquement changer la configuration du pipeline en liant un autre objet d'état du pipeline. Les détails de l'objet d'état du pipeline sont affichés dans une nouvelle fenêtre de document, avec les détails de la configuration du pipeline présentés de façon hiérarchique.  
  
### <a name="d3d12-root-signature"></a>Signature racine D3D12  
 Dans Direct3D 12, la signature racine définit toutes les ressources liées à une canalisation Graphics ou un pipeline de calcul. En outre, elle lie les listes de commandes aux ressources nécessaires aux nuanceurs. Il existe généralement une signature racine pour les graphiques et une autre pour le calcul dans une application. Les détails de la signature racine sont affichés dans une nouvelle fenêtre de document, avec les détails de la signature racine présentés de façon hiérarchique.  
  
### <a name="d3d12-resources"></a>Ressources D3D12  
 Dans Direct3D 12, les ressources sont des objets fourre-tout qui fournissent des données au pipeline de rendu. Ce comportement est différent de celui de Direct3D11, qui définissait de nombreux objets spécifiques pour différentes sortes et dimensions de ressources. Une ressource Direct3D 12 peut contenir des données de texture, des données vertex, des données de nuanceur, etc. Elle peut même représentent une cible de rendu telle que la mémoire tampon de profondeur. Les détails d'une ressource Direct3D 12 sont affichés dans une nouvelle fenêtre de document. Graphics Analysis utilise la visionneuse appropriée au contenu de l'objet de ressource, s'il peut en déterminer le type. Par exemple, un objet de ressource qui contient des données de texture est affiché à l'aide de la visionneuse de textures, exactement comme un objet Texture2D D3D11.  
  
### <a name="device-context-object"></a>Objet de contexte de périphérique  
 Dans Direct3D 11 et Direct3D 10, l’objet de contexte de périphérique (**Contexte de périphérique D3D11** ou **Périphérique D3D10**) est essentiel, car il contient les informations d’état les plus importantes. En outre, il est lié à d’autres objets d’état actuellement définis. Les détails du contexte de périphérique s’affichent dans une nouvelle fenêtre de document, et chaque catégorie d’informations est présentée dans son propre onglet. Le contexte de périphérique change lorsqu’un nouvel événement est sélectionné pour refléter l’état actuel de l’appareil.  
  
### <a name="buffer-object"></a>Objet de mémoire tampon  
 Les détails de l'objet de mémoire tampon (Mémoire tampon D3D11 ou Mémoire tampon D3D10) sont affichés dans une nouvelle fenêtre de document. Celle-ci présente le contenu de la mémoire tampon dans un tableau et fournit une interface qui permet de changer le mode d'affichage du contenu de la mémoire tampon. La table des **données de la mémoire tampon** prend en charge le copier-coller, ce qui vous permet d’utiliser un autre outil (par exemple Microsoft Excel) pour examiner son contenu. Le contenu de la mémoire tampon est interprété en fonction de la valeur de la zone de liste modifiable **format**, située au-dessus de la table des **données de la mémoire tampon**. Dans la zone, vous pouvez entrer un format de données composite incluant les types de données répertoriés dans le tableau suivant. Par exemple, « float int » affiche une liste de structures qui contiennent une valeur à virgule flottante 32 bits, suivie d'une valeur entière signée 32 bits. Les formats de données composites que vous avez spécifiés sont ajoutés à la zone de liste modifiable pour que vous puissiez les utiliser plus tard.  
  
 Vous pouvez également cocher ou décocher la case **Afficher les offsets** pour masquer ou afficher le décalage de chaque élément en mémoire tampon.  
  
|Type|Description|  
|----------|-----------------|  
|**float**|Valeur à virgule flottante 32 bits.|  
|**float2**|Vecteur qui contient deux valeurs à virgule flottante 32 bits.|  
|**float3**|Vecteur qui contient trois valeurs à virgule flottante 32 bits.|  
|**float4**|Vecteur qui contient quatre valeurs à virgule flottante 32 bits.|  
|**byte**|Valeur entière signée 8 bits.|  
|**2byte**|Valeur entière signée 16 bits.|  
|**4byte**|Valeur entière signée 32 bits. Identique à **int**.|  
|**8byte**|Valeur entière signée 64 bits. Identique à **int64**.|  
|**xbyte**|Valeur hexadécimale 8 bits.|  
|**x2byte**|Valeur hexadécimale 16 bits.|  
|**x4byte**|Valeur hexadécimale 32 bits. Identique à **xint**.|  
|**x8byte**|Valeur hexadécimale 64 bits. Identique à **xint64**.|  
|**ubyte**|Valeur entière non signée 8 bits.|  
|**u2byte**|Valeur entière non signée 16 bits.|  
|**u4byte**|Valeur entière non signée 32 bits. Identique à **uint**.|  
|**u8byte**|Valeur entière non signée 64 bits. Identique à **uint64**.|  
|**caractères**|Valeur à virgule flottante 16 bits.|  
|**half2**|Vecteur qui contient deux valeurs à virgule flottante 16 bits.|  
|**half3**|Vecteur qui contient trois valeurs à virgule flottante 16 bits.|  
|**half4**|Vecteur qui contient quatre valeurs à virgule flottante 16 bits.|  
|**double**|Valeur à virgule flottante 64 bits.|  
|**int**|Valeur entière signée 32 bits. Identique à **4byte**.|  
|**int64**|Valeur entière signée 64 bits. Identique à **8byte**.|  
|**xint**|Valeur hexadécimale 32 bits. Identique à **x4byte**.|  
|**xint64**|Valeur hexadécimale 64 bits. Identique à **x8byte**.|  
|**uint**|Valeur entière non signée 32 bits. Identique à **u4byte**.|  
|**uint64**|Valeur entière non signée 64 bits. Identique à **u8byte**.|  
|**bool**|Valeur booléenne (`true` ou `false`). Chaque valeur booléenne est représentée par une valeur 32 bits.|  
  
## <a name="see-also"></a>Voir aussi  
 [Graphics Diagnostics (débogage de DirectX Graphics)](../debugger/visual-studio-graphics-diagnostics.md)   
 [Procédure pas à pas : objets manquants en raison de l’état de l’appareil](../debugger/walkthrough-missing-objects-due-to-device-state.md)
