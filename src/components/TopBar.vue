<template>
    <div class="topbar">
        <div class="container">
            <div class="d-flex align-items-center justify-content-between">
                <div class="leftSide">
                    <a class="text-white fs-18 me-3" href="#"><i class="fa fa-facebook" aria-hidden="true"></i></a>
                    <a class="text-white font fs-18" href="#"><i class="fa fa-instagram" aria-hidden="true"></i></a>
                </div>
                <div class="d-flex align-items-center">
                    <span class="text-white fw-bold m">Shop:</span>
                    <select class="form-select form-select-sm select-shop " aria-label="Small select example">
                        <option >Select Shop</option>
                        <option  value="1">Sundon Park</option>
                        <option selected value="2">Biscod Read</option>
                    </select>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'TopBar',
    }
</script>

<style>
    .select-shop.form-select {
        background-image: none;
        padding: 3px 7px;
        cursor: pointer;
        margin-left: 10px;
        border-color: transparent !important;
    }
    .select-shop.form-select:focus {
        border-color: transparent;
        outline: 0;
        box-shadow: 0 0 0 0.25rem transparent;
    }
</style>