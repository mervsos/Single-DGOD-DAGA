# Instrucciones para actualizar el código en Google Colab

1.  **Abre un nuevo cuaderno en Google Colab.**
2.  **Clona el repositorio:**

    ```bash
    !git clone <URL_de_tu_repositorio>
    ```

3.  **Navega al directorio del repositorio:**

    ```bash
    %cd <nombre_de_tu_repositorio>
    ```

4.  **Actualiza el repositorio:**

    ```bash
    !git pull origin main
    ```

5.  **Realiza tus modificaciones.**
6.  **Confirma y sube los cambios:**

    ```bash
    !git add .
    !git commit -m "Descripción de los cambios"
    !git push origin main
    ```

7.  **configurar credenciales la primera vez:**

    ```bash
    !git config --global user.name "TuNombreDeUsuario"
    !git config --global user.email "tuemail@ejemplo.com"
    !git remote set-url origin https://<TuNombreDeUsuario>:<TuPAT>@[github.com/](https://github.com/)<TuNombreDeUsuario>/<TuRepositorio>.git
    ```

    * (Recordar generar el PAT en la pagina de github, gitlab, etc.)





# Single-Domain Generalized Object Detection

CVPR2022: Single-Domain Generalized Object Detection in Urban Scene via Cyclic-Disentangled Self-Distillation.

The current code is Faster R-CNN with FPN. In our paper, we do not utilize FPN. Besides, welcome to focus on our CVPR 2024: Prompt-Driven Dynamic Object-Centric Learning for
Single Domain Generalization. [https://github.com/Daniel00008/PDOC]

<img src='./Single-DGOD.png' width=900/>

### Datasets

#### Daytime-Sunny, Night-Sunny, Dusk-Rainy, Night-Rainy, and Daytime-Foggy

[[Download link](https://drive.google.com/drive/folders/1IIUnUrJrvFgPzU8D6KtV0CXa8k1eBV9B)]

[[models](https://drive.google.com/file/d/1s4AFraCUDX_X2ZyKthSpX0vFH37NipUY/view?usp=share_link)]

## Training

CUDA_VISIBLE_DEVICES=$GPU_ID python trainval_net_fpn.py \
                    --dataset dc_fpn --net res101 --epochs 20 \
                    --bs 2 --nw 8 \
                    --lr 0.004 --lr_decay_step 8 \
                    --cuda

## Evaluation

CUDA_VISIBLE_DEVICES=$GPU_ID python test_net_fpn.py --dataset dc_fpn --dataset_test voc_2007_train_nightclear --net res101 \
                   --checksession 1 --checkepoch 10 --checkpoint 19317 \
                   --cuda

## New Results

<img src='./Results/Results.png' width=900/>

## Citation

If you find this repository useful for your work, please cite as follows:

```
@inproceedings{wu2022single,
  title={Single-Domain Generalized Object Detection in Urban Scene via Cyclic-Disentangled Self-Distillation},
  author={Wu, Aming and Deng, Cheng},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  pages={847--856},
  year={2022}
}

```
# Single-DGOD-DAGA
