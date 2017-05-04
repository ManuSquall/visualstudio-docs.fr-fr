---
caps.handback.revision: 24
---
# D&#233;pannage de la cr&#233;ation de packages et du d&#233;ploiement SharePoint
  Cette rubrique couvre différents problèmes que vous pouvez rencontrer lorsque vous empaquetez et déployez des solutions SharePoint.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## Activation du débogage avancé  
 Pour effectuer un diagnostic entre Visual Studio, SharePoint et d'autres couches, vous pouvez utiliser la clé de Registre EnableDiagnostics afin de consulter la trace de la pile.  Pour plus d'informations, consultez [Débogage de solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## Ajout de la sortie de projet au package de solution  
 Vous pouvez ajouter la sortie de projet à un package via le Concepteur de packages.  Toutefois, lorsque vous ajoutez la sortie de projet, assurez\-vous que la plateforme du projet correspond à la plateforme de la solution SharePoint.  Nous vous recommandons d'utiliser la plateforme cible **Any CPU** pour les assemblys que vous souhaitez déployer sur un serveur SharePoint.  Pour plus d'informations, consultez [Page Compiler, Concepteur de projets &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md) et [Paramètres avancés du compilateur, boîte de dialogue &#40;Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  
  
## Erreurs et avertissements de validation  
 Les outils de développement SharePoint dans Visual Studio exécutent des étapes de validation pour vérifier que le package de solution est correctement formé.  Vous pouvez également créer des étapes de validation personnalisées pour vos fonctionnalités et vos packages.  Pour plus d'informations, consultez [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## Résolution des conflits de déploiement  
 Lorsque vous déployez une solution SharePoint, vous pouvez être confronté à des collisions lorsqu'un élément sur le serveur a un nom, une URL ou un ID identique à celui ou celle d'un élément dans votre package de solution.  Vous pouvez modifier la propriété **Deployment Conflict Resolution** pour résoudre, signaler ou ignorer des collisions relatives aux modules, aux composants WebPart, aux instances de listes et aux types de contenu.  
  
 Le tableau suivant indique les paramètres pour la propriété **Deployment Conflict Resolution**.  
  
|Valeur|Description|  
|------------|-----------------|  
|Automatique|Détecte les collisions et résout automatiquement les conflits.|  
|Prompt|Détecte les collisions et les signale au développeur avant de résoudre les conflits.|  
|None|Ne détecte pas les collisions.|  
  
## Différences entre le déploiement F5  
 Lorsque vous utilisez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour déployer votre projet SharePoint sur le serveur SharePoint local à des fins de test et de débogage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] exécute des opérations supplémentaires.  
  
1.  Réinitialisation des services IIS \(Internet Information Services\) pendant l'étape de déploiement.  
  
2.  Association automatique des flux de travail.  
  
3.  Définition de l'ordre d'activation des fonctionnalités en fonction de la hiérarchie du Concepteur de packages.  
  
 Vous pouvez ajouter des étapes de déploiement personnalisées pour modifier davantage le comportement F5.  Pour plus d'informations, consultez [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## Différer l'affichage de la page SharePoint lors du déploiement d'un composant Visual Web Part  
 L'affichage de la page SharePoint prend un certain temps lors du déploiement d'un composant Visual Web Part dans le dossier Bin sur [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] ou [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)].  Si vous modifiez des fichiers dans un répertoire [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] de niveau supérieur, tel que le répertoire bin, l'application Web entière est recompilée.  Cela peut différer de 25 secondes le rendu de la page SharePoint.  
  
### Message d'erreur  
 Aucun.  
  
### Résolution  
 Pour contourner ce problème, exécutez les étapes suivantes :  
  
1.  Installez la mise à jour KB967535 comme indiqué dans l'article du support technique Microsoft [CORRECTIF : Un correctif est disponible pour résoudre deux problèmes dans ASP.NET sur IIS 7.0 pour Windows Vista et Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055).  
  
2.  Ajoutez la ligne suivante au fichier Web.config :  
  
    ```  
    <compilation batch="false" optimizeCompilations="true">  
    ```  
  
## Le déploiement du projet SharePoint échoue avec l'erreur « Échec de l'extraction du fichier .cab dans la solution »  
 Si le nom d'un élément de projet SharePoint quelconque contient des parenthèses, le déploiement de la solution associée échoue avec une erreur.  
  
### Message d'erreur  
 Une erreur s'est produite lors de l'étape de déploiement 'Ajouter une solution' : Échec de l'extraction du fichier .cab dans la solution.  
  
### Résolution  
 Pour résoudre ce problème, supprimez les parenthèses dans les noms d'éléments de projet SharePoint.  
  
## Une erreur survient lors du déploiement d'un élément Visual Web Part sur un site d'une autre application Web  
 La première fois que vous déployez un élément Visual Web Part sur un site d'une application Web autre que celle dans laquelle il est actuellement déployé \(en modifiant la propriété SiteUrl de l'élément Visual Web Part\), vous obtenez une erreur.  
  
### Message d'erreur  
 Une erreur s'est produite lors de l'étape de déploiement 'Ajouter une solution' : Une fonctionnalité avec l'ID \[\#\] a déjà été installée dans cette batterie de serveur.  Utilisez l'attribut force pour installer à nouveau la fonctionnalité de façon explicite.  
  
### Résolution  
 Cette erreur est due au mode de retrait des fonctionnalités d'éléments Visual Web Part dans SharePoint.  Pour déployer correctement le composant Visual Web Part, déployez de nouveau la solution en choisissant la touche F5.  
  
## Un avertissement s'affiche lors du déploiement de contrôles utilisateur imbriqués  
 Cet avertissement se produit lorsque vous déployez une solution SharePoint qui contient des contrôles utilisateur imbriqués, tels qu'un composant Visual Web Part qui contient un contrôle utilisateur ou un contrôle utilisateur qui contient un composant Visual Web Part ou un autre contrôle utilisateur.  Cet avertissement se produit si vous ajoutez un contrôle à un concepteur en le faisant glisser à partir de la Boîte à outils ou en utilisant la directive @Register dans le mode Source.  
  
### Message d'erreur  
 Avertissement 1 L'élément '\[*Control Name*\]' n'est pas un élément connu.  Ceci peut se produire s'il existe une erreur de compilation dans le site Web ou si le fichier Web.config est manquant.  
  
### Résolution  
 Si le système de projet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] n'est pas informé de la présence d'un contrôle utilisateur imbriqué, il ne peut pas fournir Intellisense et il émet l'avertissement.  Le système de projet ignore la présence d'un contrôle utilisateur imbriqué si le projet n'est pas généré et que le concepteur n'est pas fermé et rouvert, ou si l'option de retrait automatique est activée, ce qui entraîne le retrait du contrôle utilisateur de la ruche SharePoint après le débogage.  
  
 Pour supprimer cet avertissement, générez le projet puis fermez et rouvrez le concepteur, ou désactivez l'option de retrait automatique pour le projet.  Pour ce faire,dans l'onglet **SharePoint** de la boîte de dialogue des propriétés du projet, désactivez la case à cocher **Retrait automatique après le débogage**.  
  
## Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  