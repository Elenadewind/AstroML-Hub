# API Documentation

## Модуль `data_ingest`

- `load_fits(path: str) -> astropy.table.Table`  
  Загружает FITS‑файл, возвращает таблицу с метаданными.
- `batch_loader(paths: List[str], chunk_size: int) -> Iterator[astropy.table.Table]`  
  Итератор для батчевой загрузки больших наборов.

## Модуль `preprocess`

- `remove_cosmic_rays(data: np.ndarray) -> np.ndarray`  
  Фильтрация космических лучей методом морфологического анализа.
- `background_subtract(data: np.ndarray) -> np.ndarray`  
  Нормализация по фону с использованием медианы.
- `interpolate_missing(data: pd.DataFrame, method: str = 'gp') -> pd.DataFrame`  
  Интерполяция пропущенных значений (метод по умолчанию: Gaussian Process).

## Модуль `feature_extraction`

- `compute_stats(flux: np.ndarray) -> Dict[str, float]`  
  Возвращает $\mu$, $\sigma$, skewness, kurtosis.
- `lomb_scargle(time: np.ndarray, flux: np.ndarray) -> np.ndarray`  
  Вычисляет периодограмму по методу Ломба‑Скаргла.
- `wavelet_coeffs(signal: np.ndarray, wavelet: str = 'db4') -> np.ndarray`  
  Возвращает вейвлет‑коэффициенты.

## Модуль `models`

- `train_classifier(X: np.ndarray, y: np.ndarray, model_type: str) -> sklearn.base.BaseEstimator`  
  Обучает классификатор (XGBoost/RF/1D‑CNN).
- `predict(model: sklearn.base.BaseEstimator, X: np.ndarray) -> np.ndarray`  
  Возвращает вероятности классов.

## Модуль `validation`

- `cross_validate_sky(data: pd.DataFrame, n_splits: int = 5) -> Dict[str, float]`  
  Кросс‑валидация по небесным секторам.
- `plot_roc(y_true: np.ndarray, y_score: np.ndarray) -> bokeh.plotting.Figure`  
  Строит ROC‑кривую.

## Модуль `output`

- `export_votable(data: astropy.table.Table, path: str)`  
  Сохраняет данные в VOTable с метаданными.
- `generate_
