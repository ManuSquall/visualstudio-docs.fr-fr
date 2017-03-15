---
title: "L’inscription du package VS | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: bebd023d8cbecf97f75570bf57ed2cd4462ffe92
ms.lasthandoff: 02/22/2017

---
# <a name="vspackage-registration"></a>Inscription du package VS
Les VSPackages doit informer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qu’ils sont installés et qu’il doivent être chargé. Ce processus est effectué en écrivant des informations dans le Registre. C’est une tâche typique d’un programme d’installation.  
  
> [!NOTE]
>  Il est une pratique acceptée pendant le développement VSPackage à utiliser l’inscription automatique. Toutefois, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] partenaires ne peuvent pas expédier leurs produits à l’aide de l’inscription automatique dans le cadre du programme d’installation.  
  
 Entrées de Registre dans un package Windows Installer sont généralement définis dans la table de Registre. Vous pouvez également enregistrer des extensions de fichier dans la table de Registre. Toutefois, Windows Installer fournit une prise en charge intégrée via l’identificateur programmatique (ProgId), classe, extension et les tables de verbe. Pour plus d’informations, consultez [les Tables de base de données](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 N’oubliez pas que vos entrées de Registre sont associées avec le composant qui est approprié pour votre stratégie côte-à-côte choisi. Par exemple, les entrées de Registre d’un fichier partagé doivent être associées au composant de Windows Installer de ce fichier. De même, les entrées de Registre pour un fichier spécifique à la version doivent être associées à composant de ce fichier. Dans le cas contraire, l’installation ou la désinstallation de votre package VS pour une version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pourrait nuire votre VSPackage dans d’autres versions. Pour plus d’informations, consultez [prenant en charge plusieurs Versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  Le moyen le plus simple pour gérer l’inscription consiste à utiliser les mêmes données dans les fichiers de mêmes pour les inscriptions pour les développeurs et inscription de l’installation. Par exemple, certains outils de développement de programme d’installation peuvent consommer le fichier au format .reg au moment de la génération. Si les développeurs gardent des fichiers .reg pour leurs propres quotidiennes de développement et débogage, ces fichiers peuvent être inclus dans le programme d’installation automatiquement. Si vous ne pouvez pas partager automatiquement les données d’enregistrement, vous devez vous assurer que la copie du programme d’installation des données d’inscription est en cours.  
  
## <a name="registering-unmanaged-vspackages"></a>L’enregistrement de packages VS non managés  
 Les VSPackages non managées (y compris ceux générés par le modèle de Package Visual Studio) utiliser les fichiers .rgs ATL-style pour stocker les informations d’inscription. Le format de fichier .rgs est spécifique à ATL et ne peut généralement être consommé en tant que-est une installation, outil de création. Informations d’inscription pour le programme d’installation du package VS doivent être gérées séparément. Par exemple, les développeurs peuvent synchroniser les fichiers .reg format avec .rgs modifications apportées au fichier. Les fichiers .reg peuvent fusionner RegEdit pour le travail de développement ou consommés par un programme d’installation.  
  
## <a name="registering-managed-vspackages"></a>L’enregistrement de packages VS managés  
 L’outil RegPkg lit les attributs de l’inscription d’un VSPackage managé et peut soit écrire les informations directement au Registre ou écrire des fichiers au format .reg qui peuvent être utilisées par un programme d’installation.  
  
> [!NOTE]
>  L’outil RegPkg n’est pas redistribuable et ne peut pas être utilisé pour inscrire un VSPackage sur le système de l’utilisateur.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Pourquoi les VSPackages ne doit pas s’inscrire au moment de l’installation  
 Les programmes d’installation de votre package VS ne doivent pas dépendre de l’inscription automatique. À première vue, en conservant les valeurs de Registre d’un VSPackage uniquement dans le VSPackage lui-même semble être une bonne idée. Étant donné que les développeurs ont besoin les valeurs de Registre disponibles pour leur travail de routine et de test, il est judicieux pour éviter de maintenir une copie distincte des données du Registre dans le programme d’installation. Le programme d’installation peut reposer sur le VSPackage lui-même pour écrire les valeurs de Registre.  
  
 Lors de la bonne en théorie, l’inscription automatique a plusieurs failles qui rendent inapproprié pour l’installation du package VS :  
  
-   Prise en charge correctement de l’installation, désinstallation, restauration de l’installation et la restauration de la désinstallation vous oblige à créer quatre actions personnalisées pour chaque VSPackage managé qui enregistre automatiquement en appelant RegPkg.  
  
-   Votre approche de prise en charge côte à côte peut nécessiter que vous créez quatre actions personnalisées qui appellent RegSvr32 ou RegPkg pour toutes les versions prises en charge de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Une installation avec les modules non inscrits ne puisse être restaurée en toute sécurité, car il n’existe aucun moyen de déterminer si les clés auto-enregistrer sont utilisées par un autre composant ou application.  
  
-   Auto-enregistrer DLL parfois des DLL auxiliaires qui ne sont pas présents ou sont une version incorrecte. En revanche, Windows Installer peut inscrire des DLL à l’aide de tables Registre sans dépendance sur l’état actuel du système.  
  
-   Code d’auto-inscription peut être refusé l’accès aux ressources réseau, telles que les bibliothèques de types, si un composant est spécifié en tant que l’exécution à partir de la source et est répertorié dans la table SelfReg. Cela peut entraîner l’installation du composant échoue pendant une installation administrative.  
  
## <a name="see-also"></a>Voir aussi  
 [Le programme d’installation de Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Inscription du Package managé](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
