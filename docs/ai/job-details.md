---
---
# <a name="view-recent-job-performance-and-details"></a>Afficher les détails et les performances des travaux récents
Une fois que les travaux sont envoyés, vous pouvez en afficher la liste pour voir leur état, leur durée et bien plus encore.

1. Dans **l’Explorateur de serveurs**, développer le contexte de calcul spécifique 
1. Double-cliquer sur **Travaux**
1. La liste des travaux envoyés à ce contexte de calcul s’affiche. 
1. Sélectionner un **travail** spécifique dans la liste pour en afficher les détails

![surveiller des travaux](media\job-details\monitor-jobs.png)

> L’historique des travaux envoyés aux machines virtuelles Linux est stocké sur la machine virtuelle dans le répertoire /tmp. Ainsi, à chaque redémarrage, l’historique des travaux est effacé. Pour conserver une trace de votre historique des travaux, configurez votre machine virtuelle en tant que contexte de calcul dans Azure Machine Learning, puis envoyez un travail à Azure Machine Learning (en sélectionnant votre machine virtuelle comme contexte de calcul).