---
title: "L’inscription du VSPackage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1405fbeba34f3e3aa9c645f6eaffe90fe6ac9036
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="vspackage-registration"></a>Inscription de VSPackage
Les VSPackages devez informer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qu’ils sont installés et qu’il doivent être chargé. Ce processus s’effectue en écrivant des informations dans le Registre. Qui est une tâche typique d’un programme d’installation.  
  
> [!NOTE]
>  Il est une pratique acceptée pendant le développement VSPackage pour utiliser l’inscription automatique. Toutefois, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] partenaires ne peut pas être commercialisé leurs produits à l’aide de l’inscription automatique dans le cadre du programme d’installation.  
  
 Entrées de Registre dans un package Windows Installer sont généralement effectuées dans la table de Registre. Vous pouvez également enregistrer des extensions de fichier dans la table de Registre. Toutefois, le programme d’installation de Windows fournit une prise en charge intégrée via l’identificateur programmatique (ProgId), classe, extension et les tables de verbe. Pour plus d’informations, consultez [des Tables de base de données](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Assurez-vous que vos entrées de Registre associées avec le composant qui est approprié pour votre stratégie côte-à-côte choisi. Par exemple, les entrées de Registre d’un fichier partagé doivent être associées au composant de Windows Installer de ce fichier. De même, les entrées de Registre pour un fichier spécifique à la version doivent être associées à composant de ce fichier. Dans le cas contraire, l’installation ou désinstallation de votre VSPackage pour une version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peut endommager votre VSPackage dans d’autres versions. Pour plus d’informations, consultez [prenant en charge plusieurs Versions de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  Pour gérer l’inscription, le plus simple consiste à utiliser les mêmes données dans les mêmes fichiers pour développeur d’enregistrement et d’inscription du moment de l’installation. Par exemple, certains outils de développement de programme d’installation peuvent consommer le fichier .reg au format au moment de la génération. Si les développeurs mettre à jour les fichiers .reg pour leur propre développement quotidienne et débogage, ces mêmes fichiers peuvent être inclus dans le programme d’installation automatiquement. Si vous ne peuvent pas partager automatiquement les données d’inscription, vous devez vous assurer que la copie du programme d’installation des données d’inscription est en cours.  
  
## <a name="registering-unmanaged-vspackages"></a>L’inscription de VSPackages non managés  
 Les VSPackages non managés (y compris celles générées par le modèle de Package Visual Studio) utiliser les fichiers .rgs style ATL pour stocker les informations d’inscription. Le format de fichier .rgs est spécifique à ATL et ne peut pas être consommé généralement en tant que-est une installation outil de création. Informations d’inscription pour le programme d’installation VSPackage doivent être gérées séparément. Par exemple, les développeurs peuvent synchroniser fichiers .reg format avec .rgs les modifications de fichier. Les fichiers .reg peuvent fusionner RegEdit pour le travail de développement ou consommées par un programme d’installation.  
  
## <a name="registering-managed-vspackages"></a>L’inscription de VSPackages gérés  
 L’outil RegPkg lit les attributs d’inscription à partir d’un VSPackage managé, et pouvez soit écrire les informations directement au Registre ou de fichiers au format .reg écriture qui peuvent être utilisés par un programme d’installation.  
  
> [!NOTE]
>  L’outil RegPkg n’est pas redistribuable et ne peut pas être utilisé pour inscrire un VSPackage sur le système d’un utilisateur.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Pourquoi les VSPackages ne doivent pas s’inscrire automatiquement au moment de l’installation  
 Les programmes d’installation de votre VSPackage ne doivent pas dépendre de l’inscription automatique. À première vue, conservation des valeurs de Registre d’un VSPackage uniquement dans le VSPackage lui-même semble être une bonne idée. Étant donné que les développeurs ont besoin les valeurs de Registre disponibles pour leurs tâches de routine et de test, il est judicieux pour éviter de maintenir une copie distincte des données du Registre dans le programme d’installation. Le programme d’installation peut reposer sur le VSPackage lui-même à écrire des valeurs de Registre.  
  
 Lors de la bonne en théorie, l’inscription automatique a plusieurs défauts qui la rendent illisible pour le VSPackage installation :  
  
-   Prise en charge correctement de l’installation, désinstallation, restauration de l’installation et la restauration de la désinstallation vous oblige à créer quatre actions personnalisées pour chaque VSPackage managé qui les enregistre en appelant RegPkg.  
  
-   Votre approche de prise en charge côte à côte peut nécessiter que vous créez quatre actions personnalisées qui appellent RegSvr32 ou RegPkg pour chaque version prise en charge de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Une installation avec les modules sont automatiquement enregistrés ne peut pas être restaurée en toute sécurité, car il n’existe aucun moyen de déterminer si les clés inscrits automatiquement sont utilisées par une autre fonction ou une application.  
  
-   Inscrit automatiquement DLL parfois des DLL auxiliaires qui ne sont pas présentes ou une version incorrecte. En revanche, le programme d’installation de Windows peuvent inscrire des DLL à l’aide de tables Registre sans dépendance sur l’état actuel du système.  
  
-   Code d’auto-inscription possible de refuser l’accès aux ressources réseau, telles que les bibliothèques de types, si un composant est spécifié en tant que l’exécution à partir de la source et est répertorié dans la table SelReg. Cela peut entraîner l’installation du composant échoue pendant une installation administrative.  
  
## <a name="see-also"></a>Voir aussi  
 [Programme d’installation de Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Inscription de Package gérée](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)