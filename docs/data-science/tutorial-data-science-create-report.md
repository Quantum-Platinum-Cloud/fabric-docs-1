---
title: Data science tutorial - create a Power BI report to visualize predictions
description: In this sixth part of the tutorial series, learn how to get set up to create reports and how to create various visuals to analyze data.
ms.reviewer: sgilley
ms.author: narsam
author: narmeens
ms.topic: tutorial
ms.custom: build-2023
ms.date: 5/4/2023
---

# Part 6: Create a Power BI report to visualize predictions

In this tutorial, we use the Microsoft Fabric DirectLake feature, which enables direct connectivity from Power BI datasets to lakehouse tables in direct query mode with automatic data refresh. In this tutorial, you'll use the prediction data produced in [Part 5: Perform batch scoring and save predictions to a lakehouse](tutorial-data-science-batch-scoring.md).

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

[!INCLUDE [prerequisites](./includes/prerequisites.md)]

* Complete [Part 1: Ingest data into a Microsoft Fabric lakehouse using Apache Spark](tutorial-data-science-ingest-data.md).  

* Optionally, complete [Part 2: Explore and visualize data using Microsoft Fabric notebooks](tutorial-data-science-explore-notebook.md) to learn more about the data.

* Complete [Part 3: Perform data cleansing and preparation using Apache Spark](tutorial-data-science-data-cleanse.md).

* Complete [Part 4: Train and register machine learning models](tutorial-data-science-train-models.md).

* Complete [Part 5: Perform batch scoring and save predictions to a lakehouse](tutorial-data-science-batch-scoring.md).

## Prepare for creating reports

1. On the left, select **OneLake data hub**.

1. Select the lakehouse that you used as part of the previous parts of the tutorial series.

1. On the top right, select Open.

   :::image type="content" source="media/tutorial-data-science-create-report/open-lakehouse.png" alt-text="Screenshot shows opening the lakehouse.":::

1. Select **New Power BI dataset** on the top ribbon and select **nyctaxi_pred**, then select **Continue** to create a new Power BI dataset linked to the predictions data you produced in part 5.

   :::image type="content" source="media\tutorial-data-science-create-report\new-power-bi-dataset.png" alt-text="Screenshot of the lakehouse UI home, showing where to select the New Power BI dataset option on the ribbon." lightbox="media\tutorial-data-science-create-report\new-power-bi-dataset.png":::

   :::image type="content" source="media\tutorial-data-science-create-report\select-predictions-data.png" alt-text="Screenshot of the New Power BI dataset dialog box, showing where to select the correct data and select Continue." lightbox="media\tutorial-data-science-create-report\select-predictions-data.png":::

1. Once the page for the new dataset loads, rename the dataset by clicking on the dropdown at top left corner of the dataset page and entering the more user-friendly name ***nyctaxi_predictions***. Click outside the drop-down to apply the name change.

   :::image type="content" source="media\tutorial-data-science-create-report\rename-dataset.png" alt-text="Screenshot of the dataset page, showing where to enter the new name." lightbox="media\tutorial-data-science-create-report\rename-dataset.png":::

1. On the dataset pane in the section titled **Visualize this data**, select **Create from scratch** and then select **Start from Scratch** to open the Power BI report authoring page.

   :::image type="content" source="media\tutorial-data-science-create-report\visualize-this-data.png" alt-text="Screenshot of the dataset pane, showing where to select Create from scratch and Start from scratch." lightbox="media\tutorial-data-science-create-report\visualize-this-data.png":::

You can now create various visuals to generate insights from the prediction dataset.

## Sample visuals to analyze predictedTripDuration

1. Create a Slicer visualization for pickupDate.

   - Select the slicer option from the visualizations pane and select ***pickupDate*** from the data pane and drop it on the created slicer visualization field of the date slider visual.

      :::image type="content" source="media\tutorial-data-science-create-report\select-slicer-option.png" alt-text="Screenshot of the visualizations pane and the data pane, showing where to select the slicer option and pickupDate data." lightbox="media\tutorial-data-science-create-report\select-slicer-option.png":::

1. Visualize Average tripDuration and predictedTripDuration by timeBins using a clustered column chart.

   - Add a clustered column chart, add ***timeBins*** to the X-axis, ***tripDuration*** and ***predictedTripDuration*** to the Y-axis and change the aggregation method to Average.

      :::image type="content" source="media\tutorial-data-science-create-report\cluster-column-chart.png" alt-text="Screenshot of the Visualizations pane and Data pane, showing where to select data for the X axis and Y axis for a clustered column chart." lightbox="media\tutorial-data-science-create-report\cluster-column-chart.png":::

1. Visualize Average tripDuration and predictedTripDuration by weekDayName.

   - Add an area chart visual and add ***weekDayName*** onto X-axis, ***tripDuration*** to Y-axis and ***predictedTripDuration*** to secondary Y-axis. Switch aggregation method to Average for both Y-axes.

      :::image type="content" source="media\tutorial-data-science-create-report\add-area-chart-visual.png" alt-text="Screenshot of the Visualizations pane and Data pane, showing where to add data to an area chart visual." lightbox="media\tutorial-data-science-create-report\add-area-chart-visual.png":::

1. Add Card visuals for overall predictedTripDuration and tripDuration.

   - Add a Card Visual and add predictedTripDuration to the fields and switch aggregation method to Average.

   - Add a Card Visual and add TripDuration to the fields and switch aggregation method to Average.

      :::image type="content" source="media\tutorial-data-science-create-report\two-card-visuals.png" alt-text="Screenshot two Visualizations panes, showing where to add to the fields. The calculations are shown below the panes." lightbox="media\tutorial-data-science-create-report\two-card-visuals.png":::

1. Visualize Average tripDuration and predictedTripDuration by pickupDate using line chart.

   - Add a line chart visual and add ***pickupDate*** onto X-axis, ***tripDuration*** and ***predictedTripDuration*** to Y-axis and switch aggregation method to Average for both fields.

      :::image type="content" source="media\tutorial-data-science-create-report\add-line-chart.png" alt-text="Screenshot of the Visualizations pane beside the resulting line chart." lightbox="media\tutorial-data-science-create-report\add-line-chart.png":::

1. Visualize Average predictedTripDuration using a map visual.

   - Add a map chart visual, and add ***startLat*** to the **Latitude** field and ***startLon*** to the **Longitude** field.

   - Add ***predictedTripDuration*** to bubble size field and switch the aggregation method of predictedTripDuration to Average.

      :::image type="content" source="media\tutorial-data-science-create-report\create-map-visual.png" alt-text="Screenshot of Visualizations pane beside the resulting map visual." lightbox="media\tutorial-data-science-create-report\create-map-visual.png":::

Once all the visuals are added, you can reshape the visuals and realign the layout based on your preferences.

:::image type="content" source="media\tutorial-data-science-create-report\reshape-realign-visuals.png" alt-text="Screenshot of all four visuals arranged together." lightbox="media\tutorial-data-science-create-report\reshape-realign-visuals.png":::

## Next steps

- [How to use end-to-end AI samples in Microsoft Fabric](use-ai-samples.md)
