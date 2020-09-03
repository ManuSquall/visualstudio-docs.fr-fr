---
title: Dépannage des VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e740860046ee9d18a137dbd513202e259e90bf79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557975"
---
# <a name="troubleshooting-vspackages"></a>Dépannage de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Voici les problèmes courants que vous pouvez rencontrer avec le VSPackage et des conseils pour résoudre les problèmes.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Pour dépanner un VSPackage qui empêche le démarrage de Visual Studio  
  
- Démarrez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en mode sans échec.  
  
     Pour démarrer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en mode sans échec, à l’invite de commandes, tapez **devenv.exe/safemode**.  
  
     Pendant ce processus, aucun VSPackages n’est chargé, à l’exception des VSPackages inclus avec [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Pour dépanner un VSPackage qui ne se charge pas  
  
1. Assurez-vous que vous utilisez la racine de Registre dans laquelle le VSPackage est inscrit pour s’exécuter, généralement la racine de Registre expérimentale.  
  
     Pour plus d’informations, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md).  
  
2. Si le VSPackage est ciblé pour s’exécuter dans la racine expérimentale du Registre, assurez-vous que vous exécutez la version expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
     Pour exécuter la version expérimentale, tapez la commande suivante dans une fenêtre de commande : **devenv/rootsuffix exp**.  
  
3. Vérifiez vos entrées de Registre VSPackage.  
  
     Pour plus d’informations, consultez [inscription de VSPackages](internals/registering-vspackages.md) et [gestion des VSPackages](../extensibility/managing-vspackages.md).  
  
4. Ouvrez la fenêtre **sortie** de l’instance de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui ne parvient pas à charger le VSPackage. Des informations sur la raison de l’échec du chargement du VSPackage peuvent s’afficher dans cette fenêtre.  
  
    > [!NOTE]
    > Si vous démarrez la version expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] à partir de l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environnement de développement intégré (IDE), examinez la fenêtre de **sortie** des deux versions.  
  
5. Examinez le journal d’activité.  
  
     Pour plus d’informations, consultez [procédure : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
6. Pour plus d’informations sur les exceptions levées par l’IDE, cliquez sur **exceptions** dans le menu **Déboguer** pour activer les exceptions. Dans la boîte de dialogue **exceptions** , sélectionnez les types d’exceptions pour lesquels vous souhaitez obtenir plus d’informations.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Pour dépanner un VSPackage qui ne s’inscrit pas  
  
1. Assurez-vous que l’assembly VSPackage se trouve dans un emplacement approuvé. RegPkg ne peut pas inscrire les assemblys dans un emplacement de confiance partielle ou non fiable, tel qu’un partage réseau dans la configuration de sécurité .NET par défaut. Bien qu’un avertissement s’affiche chaque fois qu’un utilisateur crée un projet dans un emplacement non approuvé, la case à cocher ne plus afficher ce message peut empêcher que cet avertissement se reproduise.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Pour dépanner une commande qui n’est pas visible ou qui génère une erreur lorsque vous cliquez sur une commande  
  
1. Fusionnez les commandes de menu nouvelles ou modifiées et celles déjà présentes dans l’IDE en tapant ce qui suit à l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] invite de commandes : **devenv/rootsuffix exp/Setup**.  
  
2. Assurez-vous que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] peut trouver UI.dll pour votre VSPackage.  
  
    1. Recherchez le CLSID du VSPackage dans la section packages du Registre :  
  
         HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \Packages  
  
    2. Vérifiez que le chemin d’accès spécifié par la sous-clé SatelliteDll est correct.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Pour dépanner un VSPackage qui se comporte de manière inattendue  
  
1. Définissez les points d'arrêt dans votre code.  
  
     Les bons points de départ pour le débogage sont le constructeur et la méthode d’initialisation. Vous pouvez également définir des points d’arrêt dans la zone que vous souhaitez évaluer, par exemple une commande de menu. Pour activer les points d’arrêt, vous devez exécuter sous le débogueur.  
  
    1. Dans le menu **Projet** , cliquez sur **Propriétés**.  
  
    2. Dans la boîte de dialogue **pages de propriétés** , sélectionnez l’onglet **Déboguer** .  
  
    3. Dans la zone **arguments de ligne de commande** , tapez le suffixe racine de l’environnement de développement que votre VSPackage cible. Par exemple, pour sélectionner la build expérimentale, tapez : **/RootSuffix exp**.  
  
    4. Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage** ou appuyez sur F5.  
  
        > [!NOTE]
        > Si vous déboguez un projet, créez ou chargez maintenant une instance existante de votre projet.  
  
2. Utilisez le journal d’activité.  
  
     Suivre le comportement du VSPackage en écrivant des informations dans le journal d’activité à des points clés. Cette technique est particulièrement utile lorsque vous exécutez un VSPackage dans un environnement de vente au détail. Pour plus d’informations, consultez [procédure : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
3. Utilisez des symboles publics.  
  
     Pour améliorer la lisibilité lors du débogage, vous pouvez joindre des symboles au débogueur.  
  
    1. Dans le menu **Outils/Options** , accédez à la boîte de dialogue **débogage/symboles** .  
  
    2. Ajoutez l' **emplacement de ce fichier de symboles (. pdb)**:  
  
       `https://msdl.microsoft.com/download/symbols`  
  
    3. Pour améliorer les performances, spécifiez un dossier de cache de symboles, par exemple :  

       `C:\symbols`  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Pour résoudre les problèmes liés à un VSPackage manquant ou à l’une de ses dépendances  
  
1. Pour le code managé, assurez-vous que les chemins d’accès de référence sont corrects.  
  
   1. Dans le menu **Projet** , cliquez sur **Propriétés**.  
  
   2. Sélectionnez l’onglet **références** de la boîte de dialogue **pages de propriétés** et vérifiez que tous les chemins d’accès sont corrects. Vous pouvez également utiliser l’Explorateur d' **objets** pour rechercher les objets référencés.  
  
        Pour le code managé, vous pouvez utiliser la [Fuslogvw.exe (visionneuse du journal de liaison d’assembly)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) pour afficher les détails des chargements d’assembly ayant échoué.  
  
2. Pour le code non managé, recherchez le CLSID du VSPackage dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nœud de Registre CLSID :  
  
    HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \CLSID  
  
   Assurez-vous que l’entrée InprocServer32 contient le chemin d’accès correct de la dll VSPackage.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)
