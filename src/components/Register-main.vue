<template>
    <div class="card-back">
		<div class="center-wrap">
			<Form @submit="register" class="section text-center" :validation-schema="registerFromSchema" :initial-values="formDate">
				<h4 class="mb-4 pb-3">ثبت نام</h4>
				<div class="row">
					<div class="col-md-6">
						<div class="form-group">
						<Field type="text" class="form-style" placeholder="نام و نام خانوادگی" autocomplete="off" name="name" validate-on-input="true" />
						<i class="input-icon uil uil-user"></i>
						<p class="text-danger">
							<ErrorMessage name="name"></ErrorMessage>
						</p>
					</div>	
					</div>
					<div class="col-md-6">
						<div class="form-group">
						<Field type="email" class="form-style" placeholder="ایمیل" autocomplete="off" name="email" validate-on-input="true" />
						<i class="input-icon uil uil-at"></i>
						<p class="text-danger">
							<ErrorMessage name="email"></ErrorMessage>
						</p>
					</div>
					</div>
					<div class="col-md-6">
						<div class="form-group mt-2">
							<Field type="password" class="form-style" placeholder="کلمه عبور" autocomplete="off" name="password" validate-on-input="true" />
							<i class="input-icon uil uil-lock-alt"></i>
							<p class="text-danger">
								<ErrorMessage name="password"></ErrorMessage>
							</p>
						</div>
					</div>
					<div class="col-md-6">
						<div class="form-group mt-2">
							<Field type="password" class="form-style" placeholder="تکرار کلمه عبور" autocomplete="off" name="confirmPassword" validate-on-input="true" />
							<i class="input-icon uil uil-lock-alt"></i>
							<p class="text-danger">
								<ErrorMessage name="confirmPassword"></ErrorMessage>
							</p>
						</div>
					</div>
					<div class="col-md-6">
						<div class="form-group mt-2">
							<Field type="text" class="form-style" placeholder="شماره تلفن" autocomplete="off" name="phoneNumber" validate-on-input="true"/>
							<i class="input-icon uil uil-phone"></i>
							<p class="text-danger">
								<ErrorMessage name="phoneNumber"></ErrorMessage>
							</p>
						</div>
					</div>
					<div class="col-md-6">
						<div class="form-group mt-2">
							<Field as="select" class="form-style" name="role">
								<option value="">نقش خود را انتخاب کنید</option>
								<option value="user">کاربر</option>
								<option value="teacher">مدرس</option>
							</Field>
							<i class="input-icon uil uil-subject"></i>
							<p class="text-danger">
								<ErrorMessage name="role"></ErrorMessage>
							</p>
						</div>
					</div>
					<div class="col-md-6">
						<div class="form-group mt-2" style="text-align: right;padding-right: 1rem;">
							جنسیت : 
							<label for="1">مرد</label>
							<Field type="radio" id="1" class="m-2"  value="مرد" name="gender"  />
							<label for="2">زن</label>
							<Field type="radio" id="2" class="m-2"  value="زن" name="gender" />
						</div>
					</div>
				</div>
				<button class="btn mt-4">تایید</button>
            </Form>
        </div>
    </div>
</template>

<script>
import {Form, Field, ErrorMessage} from 'vee-validate';
import {string, ref, object} from 'yup';

export default{
	components:{
		Form,
		Field,
		ErrorMessage
	},
	data() {
		const registerFromSchema = object({
			name : string().required("لطفا نام و نام خانوادگی را وارد نمایید"),
			email : string().required("ایمیل را وارد نمایید").email("ایمیل نا متعبر است"),
			phoneNumber : string().required("شماره تلفن را وارد نمایید").min(11, "شماره تلفن نامعتبر است").max(11, "شماره تلفن نامعتبر است"),
			password : string().required("کلمه عبور مورد نیازاست").min(6, "کلمه عبور باید بیشتر از 5 کاراکتر باشد"),
			confirmPassword : string().required("تکرار کلمه عبور مورد نیاز است").oneOf([ref("password"), null], "کلمه های عبور یکسان نیستند"),
			role : string().required("نوع کاربر را مشخص کنید")
		})
		return{
			registerFromSchema,
			formDate : {
				gender: "مرد",
				role : "user"
			}
		};
	},
	methods : {
		register(values){
			console.log(values);
		},
	}
}

</script>

<style>

</style>
