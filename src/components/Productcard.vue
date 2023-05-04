<script>
export default {
	props: {
		products: { type: Object, required: true },
	},
};
</script>
<template>
	<div class="d-flex">
		<div class="p-1 d-fex flex-column">
			<img :src=" products.img[0]" alt="img" width="100">
		</div>
        <div>
            <div class="p-1">
                <strong>Thể loại:</strong>
                {{products.categories}}
            </div>
            <div class="p-1">
                <strong>Lượt xem:</strong>
                {{products.price}}
            </div>
            <div class="p-1">
                <strong>Tên tác giả:</strong>
                {{products.color}}
            </div>
            <div class="p-1">
                <strong>Tình trạng:</strong>
                {{products.size}}
            </div>
        </div>
	</div>
</template>
