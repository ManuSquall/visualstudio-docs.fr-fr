---
title: "Comment&#160;: personnaliser un VSPackage (C# et Visual Basic) | Microsoft Docs"
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
  - "Boîte de dialogue À propos de"
  - "VSPackages, écrans de démarrage"
  - "VSPackages, personnalisation"
ms.assetid: 705a41c3-63d6-4c1e-9f82-771be9191579
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Comment&#160;: personnaliser un VSPackage (C# et Visual Basic)
Pour afficher dans la boîte de dialogue de **À propos de** et l'écran de démarrage, VSPackages doit implémenter l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> .  Cela fournit les informations suivantes dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Nom  
  
-   ID, tel que l'interface série ou le numéro de version  
  
-   Information  
  
-   icône de logo  
  
 Le code suivant est de [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md).  
  
### pour implémenter l'interface d'IVsInstalledProduct  
  
1.  ajoutez l'attribut d' <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> à la classe qui implémente le VSPackage.  cette classe doit dériver d' <xref:Microsoft.VisualStudio.Shell.Package> et d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>.  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_1.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_1.vb)]  
  
     Premier argument, <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute.UseInterface%2A>, de l'attribut d' <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> indique [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] d'utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> pour obtenir des informations sur le produit, au lieu de la clé de Registre d'InstalledProducts.  Les arguments restants sélectionnent des ressources de type chaîne pour afficher le nom de produit, les informations, et l'ID, respectivement.  Toutefois, étant donné que le premier argument est `true`, les arguments restants sont `null`.  
  
2.  Cliquez avec le bouton droit sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>, pointez sur **Implémenter l'interface**, puis cliquez sur **Implémenter l'interface**.  
  
3.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> à l'aide de le code suivant.  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_2.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_2.vb)]  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] appelle ces méthodes pour obtenir des informations pour stigmatiser le VSPackage.  la méthode de GetResourceString est utilisée pour localiser ces informations.  
  
    > [!NOTE]
    >  Les commentaires de code sont supprimés par souci de concision.  vous pouvez les rechercher dans [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md).  
  
### Pour stocker les chaînes de les informations de produit  
  
1.  Double\-cliquez sur le fichier de ressources .resx associé au VSPackage.  
  
     l'éditeur de ressources s'ouvre.  
  
2.  Rechercher ou ajoutez le nom de produit, les informations, et ID.  
  
     Les chaînes de ressources suivantes sont de [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md).  
  
     @101  
     Écran de démarrage et aide de package sur le nom officiel \(c\#\).  
  
     @102  
     Ce package montre comment afficher du texte et à l'image de l'écran de démarrage et d'aide sur.  
  
     @104  
     8.0  
  
3.  Sélectionnez et remplacez ces informations que vous le souhaitez.  
  
### Pour gérer les icônes et les bitmaps de produit  
  
1.  Ajoutez les bitmaps et les icônes du projet en tant que ressources du projet.  
  
     Pour plus d'informations, consultez [NOT IN BUILD: Adding and Editing Resources \(Visual C\#\)](http://msdn.microsoft.com/fr-fr/95f15d03-bed0-410c-8d1f-dece5199ba1e).  
  
2.  Fermez l'éditeur de ressources et rouvrez le fichier .resx dans XML ou un éditeur de texte.  
  
    > [!NOTE]
    >  L'éditeur de ressources ne prend pas en charge les assignation des identificateurs de ressource aux éléments autres que des chaînes.  
  
3.  Rechercher ou ajoutez l'icône et les ressources bitmap au fichier .resx.  les ressources suivantes sont de [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md).  
  
    ```  
    <data name="300" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.bmp;System.Drawing.Bitmap, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    <data name="400" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.ico;System.Drawing.Icon, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    ```  
  
### Pour tester la boîte de dialogue about et les écrans de démarrage  
  
-   Pour tester votre VSPackage, consultez [Comment : tester la boîte de dialogue À propos de du menu Aide et l’écran de démarrage](../misc/how-to-test-the-help-about-and-splash-screens.md).  
  
## Voir aussi  
 [Personnalisation de VSPackage](/visual-cpp/misc/vspackage-branding)